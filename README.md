# VSCode Logstash Editor

Visual Studio Code extension that provides completion, documentation and auto-formatting for Logstash pipeline configuration files, logstash.yml, pipelines.yml and Elasticsearch index template json files.

![Example](images/example.png)

[Project Page](https://github.com/fbaligand/vscode-logstash-editor)  
[Change Log](https://github.com/randomchance/vscode-logstash-configuration-syntax/blob/master/CHANGELOG.md)


## Features

- Provides completion for Logstash pipeline configuration files (sections, plugins, options), depending current cursor position.  
For example, if cursor is inside `grok` filter, options for `grok` filter are suggested.
- All completion data is generated from official Logstash documentation
- Options for a plugin are sorted : first required options, then optional specific options, and finally optional common options
- When you preselect an item, a link to official documentation, a short description and an example (if available) are provided
- If you choose a completion item, a code snippet is automatically inserted with relevant content:
  - for a plugin, inserted snippet is the plugin block and all its required options
  - for an option, inserted snippet is based on option type (string, boolean, number, string_duration, array, hash)
- Provides completion for if statement
- Provides documentation when hover on a section, a plugin or an option
- Provides document formatting and document range formatting on a Logstash pipeline configuration file
- Provides completion for "logstash.yml" and "pipelines.yml" files
- Provides completion for Elasticsearch index template json files, based on a json schema
- Provides a specific index template json schema for Elasticsearch 6.x and 7.x
- Provides "logstash.version" configuration setting to choose Logstash version (for completion)
- Provides "Set Logstash Version" command (shortcut: Ctrl+Shift+L) to change Logstash version setting
- Supported Logstash versions: 6.8, 7.2, 7.5, 7.9
- Following file patterns are automatically associated to Logstash language:
  - `*logstash.conf`
  - `*logstash.conf.j2`
  - `*logstash.conf.template`
  - `logstash-*.conf`
- Following file patterns are automatically associated to Elasticsearch index template json schema:
  - `*elasticsearch-template.json`
  - `*elasticsearch-template-es7x.json`
  - `*elasticsearch-template-es6x.json`


## Syntax highlighting

This extension does not provide syntax highlighting for Logstash configuration files, because this feature is already provdided by [Logstash Configuration Syntax / Language Support](https://marketplace.visualstudio.com/items?itemName=RandomChance.logstash) extension.  
So this extension is recommended to complete this one.


## Important note

For now, only this format style is supported for Logstash configuration files:
``` ruby
filter {
	tcp {
		port => 12345
	}
}
```

This format style is not supported:
``` ruby
filter 
{
	tcp 
	{
		port => 12345
	}
}
```

Neither this one:
``` ruby
filter { tcp { port => 12345 } }
```
