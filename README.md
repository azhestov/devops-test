setup CI pipeline in GitHub for demo UE5 project (FPS game template).
1. At each commit to main branch it compiles the editor libraries:
   "%UE_ROOT%\Engine\Build\BatchFiles\Build.bat" DevopsTestEditor Win64 Development -project=%cd%\DevopsTest.uproject
3. Each night it packages the project with this command:
   "%UE_ROOT%\Engine\Build\BatchFiles\RunUAT.bat" BuildCookRun -project=%cd%\DevopsTest.uproject -noP4 -platform=Win64 -clientconfig=Development -build -cook -stage -pak -archive -archivedirectory=$(Build.StagingDirectory)
5. (Optionally) After step 2 it compresses the result and uploads it to Build Artifacts
UE_ROOT points to the engine instalation directory. 
