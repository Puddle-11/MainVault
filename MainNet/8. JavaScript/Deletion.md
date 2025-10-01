<%*
const targetFolder = "MainNet/7. Deleted"; // folder name in your vault
const activeFile = tp.app.workspace.getActiveFile();

if (!activeFile) {
    new Notice("No active file!");
} else {
    // 1️⃣ Move the file
    const newPath = `${targetFolder}/${activeFile.name}`;
    await tp.app.fileManager.renameFile(activeFile, newPath);

    // 2️⃣ Update YAML frontmatter with Date Deleted
    const fileCache = tp.app.metadataCache.getFileCache(activeFile);
    const yaml = fileCache?.frontmatter || {};

    // Set "Date Deleted" to today in YYYY-MM-DD format
    const today = new Date();
    const yyyy = today.getFullYear();
    const mm = String(today.getMonth() + 1).padStart(2, '0');
    const dd = String(today.getDate()).padStart(2, '0');
    yaml["Date Deleted"] = `${yyyy}-${mm}-${dd}`;

    // Rebuild frontmatter string
    const yamlString = `---\n${Object.entries(yaml).map(([k,v]) => `${k}: ${v}`).join("\n")}\n---\n`;

    // Read current content and remove old frontmatter
    const content = await tp.app.vault.read(activeFile);
    const contentWithoutYaml = content.replace(/^---\n[\s\S]*?\n---\n/, "");

    // Write back updated frontmatter + content
    await tp.app.vault.modify(activeFile, yamlString + contentWithoutYaml);

    new Notice(`Moved ${activeFile.name} to ${targetFolder} and set Date Deleted to ${yaml["Date Deleted"]}`);
}
%>