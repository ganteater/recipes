# Anteater Recipe Examples

Repository URL: [https://svn.code.sf.net/p/anteater/code/trunk/ae-samples/recipes](https://svn.code.sf.net/p/anteater/code/trunk/ae-samples/recipes)

## Recipe Scanning

The Anteater project scans recipe files by &lt;Recipes&gt; tag in the environment configurations file: **ae.xml**. 
&lt;Recipes&gt; tag can to search recipe files in a folder witch defined by the path attribute.
It can be absolute path to folder, relative path with ae.xm location base folder or path to zip archive. 

Recipes ia scanning by the following priority ordering:

1. Configuration definition: last &lt;Recipes&gt; is have higher priority and will override all others.
2. Default recipes witch you can save in anteater application jar file.

Bellow you can see example of anteater project with several recipes level:
    

```
ae-project
├── ae.bat 
├── anteater.jar 
│ ├── recipes # low (default) level
│ │ ├── About.recipe 
│ │ ├── Append.recipe 
│ │ └── ... 
│ └── ... 
├── recipes.zip 
│ ├── About.recipe 
│ ├── Append.recipe 
│ └── ... 
├── recipes/ # high level
│ ├── About.recipe 
│ ├── Append.recipe 
│ └── ... 
└── ae.xml
```

ae.xml:

```xml
<Environment xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:noNamespaceSchemaLocation="https://raw.githubusercontent.com/viktor-tovstyi/maven/refs/heads/repo/ae.xsd">
	<Configuration name="My Configuration" userPreferencesEncryption="false">
		...
		<Recipes path="https://sourceforge.net/code-snapshots/svn/a/an/anteater/code/anteater-code-r630-trunk-ae-samples-recipes.zip"/>
		<Recipes path="recipes.zip" /> 
		<Recipes path="recipes" />
		...
	</Configuration>
</Environment>
```

As usual the anteater recipe identified by the name and you can save you file wher you want and you can change location if it is needed. If Anteater detected two files with equals name will by raise a user dialog interface component during configuration load:

![Recipe Name Conflict](https://a.fsdn.com/con/app/proj/anteater/screenshots/recipe-names-conflict-78713424.png)   