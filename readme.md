# O3DE MultiPlayerSample Assets

This repository contains:

1. A collection of O3DE Asset Gems, used in o3de-multiplayersample project
   1. The source gem folder for development
2. A `repo.json` file containing information about this O3DE Remote Gem Repository
3. A GitHub release folder
   1. The gem .zip containing the gem and associated gem.json for each gem

## If you are using o3de-multiplayer sample

These gems are required for and utilized by the o3de-multiplayer sample project, you can find the repo and instructions for that project and adding these gems here:

[GitHub - o3de/o3de-multiplayersample: Multiplayer sample project for the Open 3D Engine](https://github.com/o3de/o3de-multiplayersample)

## If you want to use these Gems in your own o3de project

### Option #1. Remote Repository, use packaged Gems with the Project Manager

**<u>( Use of this as a remote gem repository is not yet implemented )</u>**

Add this remote repository in the Project Manager using this URL

```
https://raw.githubusercontent.com/AMZN-alexpete/o3de-remote-gem-repo-demo/main
```

You can then browse the gems in the Project Manager and add them to your Project.

### Option #2.  Download and use source Gems

You can clone and download the repository source, then register the local gem source folders with the engine to make available for use in a Project.  This entails the same steps as a developer contributing content creation or performing other maintenance of the gem data. (see the next section below.)

## If you are a developer contributing to these asset gems

### Download and Install

This repository uses Git LFS for storing large binary files.  You will need to create a Github personal access token to authenticate with the LFS service.

#### Create a Git Personal Access Token

You will need your personal access token credentials to authenticate when you clone the repository.

[Create a personal access token with the 'repo' scope.](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

#### (Recommended) Verify you have a credential manager installed to store your credentials

Recent versions of Git install a credential manager to store your credentials so you don't have to put in the credentials for every request. It is highly recommended you check that you have a [credential manager installed and configured](https://github.com/microsoft/Git-Credential-Manager-Core)

#### Step 1. Clone the repository

You can clone the project to any folder locally, including inside the engine folder. If you clone the project inside an existing Git repository (e.g. o3de) you should add the project folder to the Git exclude file for the existing repository.ne-the-repository)

##### Option #1 (Highly Recommended) - cloning into a folder outside the engine repository folder

```shell
# clone the project into a folder outside your engine repository folder
> git clone https://github.com/o3de/o3de-multiplayersample-assets.git
Cloning into 'o3de-multiplayersample-assets'...
```

##### Option #2 - cloning into the engine repository folder

```shell
# clone the project into a folder named 'o3de-multiplayersample' in your existing engine repository folder
> git clone https://github.com/o3de/o3de-multiplayersample-assets.git c:/path/to/o3de/o3de-multiplayersample-assets
Cloning into 'o3de-multiplayersample'...

# modify the local engine git exclude file to ignore the project folder
> echo o3de-multiplayersample-assets > c:/path/to/o3de/.git/info/exclude
```

If you have a Git credential helper configured, you should not be prompted for your credentials anymore.

### Step 2. Register the gems with the engine

You may have already done this, these are the same steps as setting up the o3de-multiplayer sample project.  But if you are adding them to your own project these are the steps to do so.

Make sure your engine is registered.

```shell
# register the gems with the engine, you only need to do this once
> c:/path/to/o3de/scripts/o3de register --this-engine
```

Make sure your project is registered.

```shell
# register the project with the engine, you only need to do this once
> c:/path/to/o3de/scripts/o3de register -p c:/path/to/o3de-multiplayersample'
```

Now make sure that the source gems are registered

```shell
# register the gems with the engine, you only need to do this once
> o3de register --all-gems-path c:/path/to/o3de-multiplayersample-assets/Gems
```

 The above command will recursively scan the input path, then registers all paths with gem.json files into the ~/.o3de/o3de_manifest.json

Now these Gems will be available in the Project Manager and can be added to your Project.

# Appendix

How these were made.

```
cd c:\o3de
scripts\o3de create-gem --gem-path C:\Gems\TestGem --template-path C:\o3de\Templates\AssetGem
```
