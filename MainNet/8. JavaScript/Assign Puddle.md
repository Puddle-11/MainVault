<%*

const activeFile = tp.app.workspace.getActiveFile();

if (!activeFile) {
    new Notice("No active file!");
} else {

  const content = await tp.app.vault.read(activeFile);
  const yamlMatch = content.match(/^---\n([\s\S]*?)\n---\n?/);

const user = "Puddle";
  const today = new Date();
  const yyyy = today.getFullYear();
  const mm = String(today.getMonth() + 1).padStart(2, '0');
  const dd = String(today.getDate()).padStart(2, '0');

  const dateLine = `Date Assigned: ${yyyy}-${mm}-${dd}`;
	const userLine = 'User: Puddle';
  let newContent;
  
  if (yamlMatch) 
  {
    let yamlBody = yamlMatch[1];

    if (/^\s*Date Assigned:/m.test(yamlBody)) 
    {
      yamlBody = yamlBody.replace(/(^\s*Date Assigned:.*$)/m, dateLine);
    } 
    else 
    {
      yamlBody = yamlBody.replace(/\s+$/s, ''); 
      yamlBody = yamlBody + `\n${dateLine}`;
    }
	if(/^\s*User:/m.test(yamlBody)){
	yamlBody = yamlBody.replace(/(^\s*User:.*$)/m, userLine);
	}
	else{
	  yamlBody = yamlBody.replace(/\s+$/s, ''); 
      yamlBody = yamlBody + `\n${userLine}`;
	}


    const tail = content.slice(yamlMatch[0].length);
    newContent = `---\n${yamlBody}\n---\n${tail}`;
  } 
  else 
  {
    newContent = `---\n${dateLine}\n---\n\n${content}`;
  }


  await tp.app.vault.modify(activeFile, newContent);

  new Notice(`set Date Assigned to ${yyyy}-${mm}-${dd}`);

}
%>