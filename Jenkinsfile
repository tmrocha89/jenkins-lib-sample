def Config = [
    "type" : "c#",
    "solution" : "DeleteMe_Test001.sln"
]


node{

    def msbuildTool = tool 'msbuild'
    win.thebatman.tmrjenkinslib.platformRunners.IPlatformRunner runner = new win.thebatman.tmrjenkinslib.platformRunners.WindowsPlatformRunner(this);


    stage('build'){
        win.thebatman.tmrjenkinslib.compilers.ICompiler compiler = new win.thebatman.tmrjenkinslib.compilers.MsBuildBuilder(msbuildTool, this, runner);
        bat "dir"
        compiler.addProject(Config["solution"])
                .setToRebuild()
                .run();
    }



}