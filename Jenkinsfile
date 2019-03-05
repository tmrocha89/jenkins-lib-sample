def Config = [
    "type" : "c#",
    "solution" : "DeleteMe_Test001.sln"
]


node{

    def msbuildTool = tool 'msbuild'
    win.thebatman.tmrjenkinslib.platformRunners.IPlatformRunner runner = new win.thebatman.tmrjenkinslib.platformRunners.WindowsPlatformRunner(this);

    SafeStage('checkout'){
        win.thebatman.tmrjenkinslib.versionControl.IVersionControlSystem git = new win.thebatman.tmrjenkinslib.versionControl.GitVersionControlSystem(this, runner);
        git.CloneCurrentProject()
    }

    SafeStage('build'){
        win.thebatman.tmrjenkinslib.compilers.ICompiler compiler = new win.thebatman.tmrjenkinslib.compilers.MsBuildBuilder(msbuildTool, this, runner);
        compiler.addProject(Config["solution"])
                .setToRestore()
                .setToRebuild()
                .run();
    }

    SafeStage('Tests'){
        echo "Not implemented yet"
    }

    SafeStage('Deploy'){
        echo "Deploying app"
        win.thebatman.tmrjenkinslib.compilers.ICompiler compiler = new win.thebatman.tmrjenkinslib.compilers.MsBuildBuilder(msbuildTool, this, runner);
        compiler.addProject(Config["solution"])
        .setToRebuild()
        .setDeployOnBuild()
        .setPublishProfileByName("testtmdeploy - Web Deploy")
        .setPassword("azure_deleteproject_envXPTO")
        .setConfiguration("Release")
        .run();
    }

    SafeStage('Checking Availability'){
        echo "Checking if app is alive"
    }

}