def Config = [
    "type" : "c#",
    "solution" : "DeleteMe_Test001.sln"
]


node{

    def msbuildTool = tool 'msbuild'
    win.thebatman.tmrjenkinslib.platformRunners.IPlatformRunner runner = new win.thebatman.tmrjenkinslib.platformRunners.WindowsPlatformRunner(this);

    stage('checkout'){
        win.thebatman.tmrjenkinslib.versionControl.IVersionControlSystem git = new win.thebatman.tmrjenkinslib.versionControl.GitVersionControlSystem(this, runner);
        git.CloneCurrentProject()
    }

    stage('build'){
        win.thebatman.tmrjenkinslib.compilers.ICompiler compiler = new win.thebatman.tmrjenkinslib.compilers.MsBuildBuilder(msbuildTool, this, runner);
        compiler.addProject(Config["solution"])
                .setToRestore()
                .setToRebuild()
                .run();
    }

    stage('Tests'){
        echo "Not implemented yet"
    }

    stage('Deploy'){
        echo "Deploying app"

        //withCredentials([string(credentialsId: 'azure_deleteproject_envXPTO', variable: 'PASSWORD')]) {
            win.thebatman.tmrjenkinslib.compilers.ICompiler compiler = new win.thebatman.tmrjenkinslib.compilers.MsBuildBuilder(msbuildTool, this, runner);
            compiler.addProject(Config["solution"])
            .setToRebuild()
            .setDeployOnBuild()
            .setPublishProfileByName("testtmdeploy - Web Deploy")
            .setPassword("azure_deleteproject_envXPTO")
            .setConfiguration("Release")
            .run();
        //}

    }

    stage('Checking Availability'){
        echo "Checking if app is alive"
    }

}