### CTS Tools Overview

This workspace contains CTS specific tools and documents.  The tools and documents within the workspace are not part of the Java EE CTS package that is shipped to customers.  

The workspace currently has 2 directories - docs and tools. The docs directory contains CTS developer documents as well as XSL style sheets and DTDs used in the assertion list generation.  The tools directory contains all the CTS tools, set of library jars used by the CTS tools, set of java utility classes, and useful shell scripts. 

### How to build CTS tools in this workspace ?
Install Apache Ant and set an envronment variable ANT_HOME. Set <ANT_HOME>/bin to PATH variable. 
```
cd TS_TOOLS_HOME/tools
ant 
```

*Note :* If you are a TCK developer and would like to add a tool to the workspace simply create a new directory under the tools directory and add your tool.  You must follow some simple guidelines when adding a new tool. 
  - All tools must be built using Ant.
  - You must have a src directory in your tool directory with all the source code placed in the directories that mimic the package declarations in the source file.
  - Your Ant build file should compile the java source and place it into a classes directory under your tool directory.
  - If you have a distribution feel free to create a dist directory and add a target to the ant build file to create the distribution.  If you have any shell scripts included with your tool place them into a scripts directory.  
  - It is nice if you include a README file at the top level to let people know what the tool is and how it works.
  - If you want your tools to be built with all the other tools, add an ant call in the build.xml file located in the tools directory, you can also add a clean ant call as well to remove your built tool.
  - At a minimum all ant build files should have a compile and clean target with compile being the default target.

Recommended directory structure:

```
  tools
   |
   |__ build.xml (builds all tools and scripts in tools directory)
   |
   |__ your-tool-dir
             |
             |__ build.xml
             |
             |__ src
             |    |
             |    |__ com/sun/cts/your-package-name/*.java
             |
             |__ classes (generated by ant build)
             |
             |__ dist (generated by ant build)
             |
             |__ scripts
                  |
                  |__ *.sh, *.bat
```

If you have an XSL style sheet or DTD to add to the gate place them under docs/xsl and docs/dtd respectively.