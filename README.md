Run web application in tomcat with additional features:

-	additional classpath entries

-	directory mapping

Webapp-runner works by creating a tomcat configuration 
in temporary (or configured) CATALINA_BASE directory.
Additional classpath entries are configured using 
`shared.loader` key in `conf/catalina.properties` files.
Directory mappings are made with `PostResources`-tags
in `conf/Catalina/localhost/ROOT.xml`.



	Webapp Runner

	Usage:
	  webapp-run (-h|--help)
	  webapp-run (-w|--webapp) <webapp> [-p|--port <port>] [-C|--context <path>] [-c|-cp|--classpath <path>] [-m|--map <resource> <path>] [-n|--no-run]

	Options:
	  -h --help                   Show this screen.
	  -w --webapp <webapp>        WAR or expanded WAR
	  -p --port <port>            Port to listen
	  -C --context <path>         Webapp context path
	  -c -cp --classpath <path>   Add   
	  -m --map <resource> <path>  Map external resource on webapp path
	  -k --config-only            do not run tomcat, only configure CATALINA_BASE
	  -r --run-only               do not configure CATALINA_BASE, just run tomcat from it

	Environment variables:
	  ASSET_DIR                   Directory containing files additional to this script.
	                              By default the directory where script is located.
	  PATH_SEPARATOR              Path separator used to parse classpaths, colon (:) by default.
	  TEMP                        Base for temporary directory to create CATALINA_BASE
	                              (not used if CATALINA_BASE is set explicitly)
	  CATALINA_HOME               Tomcat 8 installation directory (required)
	  CATALINA_BASE               If set, use this directory, not create temporary in TEMP
	  SHUTDOWN_PORT               That is to be configured in tomcat, 
	                              by default random port in the range 10000-65000 is selected
	  REALPATH_COMMAND            command to convert relative paths to absolute before writing to config files, 
	                              default realpath itself
	  STARTUP_COMMAND             command to start tomcat, default "${CATALINA_HOME}/bin/startup.sh"

	Configuration files
	  webapp-runner loads configuration from /etc/webapp-runner-env then from ~/.webapp-runner-env
	  usung bash sourcing.

	Cygwin notes
	  When running on cygwin you may need to adjust some variables, for example:
	  export REALPATH_COMMAND='cygpath -aw'
	  export STARTUP_COMMAND='cmd.exe /C C:\tomcat-8.5\bin\startup.bat'