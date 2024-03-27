<table>
  <tr>
  </tr>
<tr>
    <td valign="center">
      <h2 align="center">Toolkit for Devs Using Arch-Linux</h2>
      <ol>
        
  <a href="#clearing-unwanted-files-in-arch-linux">Clearing Unwanted Files in Arch Linux</a>
        
  <a href="#updating-github-repositories-with-local-changes">Updating GitHub Repositories with Local Changes</a>

   </ol>
    </td>
    <td align="right" valign="center">
      <img src="https://github.com/AlexandrosLiaskos/ArchDevKit/assets/128935863/5c851391-55da-4122-8f59-6c87f296e1a1" width="300px">
    </td>
  </tr>
</table>

![bulbasaur-y5-3440x1440](https://github.com/AlexandrosLiaskos/ArchDevKit/assets/128935863/e35953aa-aecf-419e-804d-086012e8faa6)


# Clearing Unwanted Files in Arch Linux

Efficient disk space management is crucial for maintaining optimal performance. Accumulation of unwanted files can lead to a full root partition, impacting system efficiency. This article outlines my personal practical method for identifying and clearing these files.

#### Identifying Unwanted Files

Use the `du` command to identify directories and files consuming significant disk space. For a high-level overview of top-level directories, execute:

```bash
sudo du -h --max-depth=1 / | sort -h
```

For a detailed view of all directories and files, use:

```bash
sudo du -h | sort -h
```

To inspect a specific directory, replace `<directory-path>` with the target directory's path:

```bash
sudo du -h <directory-path> | sort -h
```

#### Deleting Unwanted Files

After identifying the unnecessary files, use the `rm` command for deletion. For example:

```bash
sudo rm -rf <directory-path>
```

Ensure to replace `<directory-path>` with the appropriate path. Exercise caution with `rm -rf` as it permanently deletes files without confirmation.

To clear the trash directory, execute:

```bash
rm -rf ~/.local/share/Trash/files/*
```

#### Additional Disk Space Management

For further disk space optimization, utilize `pacman` to clean up package caches. The command below removes cached versions of installed and uninstalled packages, retaining only the latest three:

```bash
sudo pacman -Sc
```

![unmcgmc defined - Imgur](https://github.com/AlexandrosLiaskos/ArchDevKit/assets/128935863/cfd3d94b-66ea-41ff-b9df-aa954f46fc0c)


# Updating GitHub Repositories with Local Changes

Managing and synchronizing changes between your local directory and your GitHub repository is a common task for developers. This guide is divided into two main sections: **First-Time Setup** and **Standard Update Process**. The first-time setup is for when you're connecting your local directory to a GitHub repository for the first time. The standard update process is what you'll follow for routine updates after the initial setup.

### CLI environment setup 

Follow the manual for the installation and further configuration of the necessary authentication with your Github account:

[Manual](https://cli.github.com/manual/)


> [!NOTE] SSH/HTTP
> Both options can be used and won't affect anything. Personally I have used SSH and I have set a passphrase that works as a password each time I execute commands that interact with my repository.

### First-Time Setup

The first-time setup involves a series of steps to connect your local directory with your GitHub repository. This is a one-time process for each repository.

#### 1. Clone the Repository (Optional)

If you're starting with an existing GitHub repository, clone it to your local machine:

bashCopy code

`gh repo clone <repository-url>`

Replace `<repository-url>` with the actual URL of your GitHub repository.

#### 2. Initialize a New Git Repository
If you're starting with a local directory that isn't yet a Git repository, initialize it:

bashCopy code

`cd path/to/your/directory git init git branch -m main`

#### 3. Connect to GitHub

Link your local repository to your GitHub repository:

bashCopy code

`git remote add origin <repository-ssh-url>`

Replace `<repository-ssh-url>` with your repository's SSH URL.

#### 4. Initial Pull (Optional)

To avoid conflicts, pull any existing content from the GitHub repository (useful if you initialized a new git repository):

bashCopy code

`git pull origin main --rebase`

### Standard Update Process

After the initial setup, use the following standard process to update your GitHub repository with new changes from your local directory.

#### 1. Pull Latest Changes (Optional but Recommended)

This step ensures your local repository is up-to-date. It's especially important if there are others contributing to the repository:

bashCopy code

`git pull origin main --rebase`

#### 2. Add Changes

Add the changes you want to commit to the staging area:

bashCopy code

`git add .`

Or, to add specific files:

bashCopy code

`git add path/to/your/file`

#### 3. Commit Changes

Commit your staged changes to your local repository:

bashCopy code

`git commit -m "Your commit message"`

Replace `"Your commit message"` with a meaningful description of your changes.

#### 4. Push Changes to GitHub

Finally, push your committed changes to GitHub:

bashCopy code

`git push origin main`

#### Conclusion

Following this guide, you can efficiently manage and synchronize your local changes with your GitHub repository. Remember, the first-time setup is only necessary once per repository. After that, the standard update process will be your routine workflow for updating your GitHub repository.


