<%*

const targetFolder = "MainNet/1. Main Notes"; 
const activeFile = tp.app.workspace.getActiveFile();
const propertyToRemove = "Date Deleted";

if (!activeFile) {
    new Notice("No active file!");
} else {
let content = await app.vault.read(activeFile);
  const newPath = `${targetFolder}/${activeFile.name}`;
  await tp.app.fileManager.renameFile(activeFile, newPath);

  const yamlRegex = /^---\n([\s\S]*?)\n---/;
  const match = content.match(yamlRegex);
  if (match) {
    let yamlContent = match[1];

    const newYaml = yamlContent
        .split("\n")
        .filter(line => !line.trim().startsWith(propertyToRemove + ":"))
        .join("\n");


    content = content.replace(yamlRegex, `---\n${newYaml}\n---`);
    
    await app.vault.modify(activeFile, content);
    
  } 
  else {
    
  }
}

%>