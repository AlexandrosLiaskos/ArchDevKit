![ArchDevKit Banner](https://github.com/YourUsername/ArchDevKit/assets/banner.jpg)

<table>
  <tr>
  </tr>
<tr>
    <td valign="center">
      <h2 align="center">Toolkit for Devs Using Linux</h2>
      <ol>
        
  <a href="#clearing-unwanted-files-in-arch-linux">Clearing Unwanted Files in Arch Linux</a>
        
  <a href="#updating-github-repositories-with-local-changes">Updating GitHub Repositories with Local Changes</a>

   </ol>
    </td>
    <td align="right" valign="center">
      <img src="https://github.com/YourUsername/ArchDevKit/assets/logo.png" width="300px">
    </td>
  </tr>
</table>

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

