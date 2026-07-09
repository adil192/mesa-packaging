### [adil192/mesa-x86-64-v3](https://copr.fedorainfracloud.org/coprs/adil192/mesa-x86-64-v3/)

Almost-stable releases of mesa3d graphics drivers: get the newest features with the fewest bugs.

Use at your own risk! Check requirements!

#### Requirements

These mesa builds are optimized for - and require - modern x86-64-v3 CPUs. 

If your CPU is not compatibile, you will break your system!

Check first by running `ld.so --help` in a terminal. It should output something like this:
```
...
Subdirectories of glibc-hwcaps directories, in priority order:
  x86-64-v4
  x86-64-v3 (supported, searched)		<-- IT MUST SAY SUPPORTED HERE
  x86-64-v2 (supported, searched)
```

#### Why this repo exists...

I wanted newer versions of mesa before they landed in Fedora's official repos.

Newer versions are *occasionally* much faster than their predecessors.
For example, Mesa 26.0 brought significant Radeon raytracing performance improvements.

This repo also gets bug fixes faster than Fedora.
For example, Mesa 26.2.1 fixed graphical corruption when playing YouTube AV1 videos.

#### Compared to other repos...

**Choose this repo if**:
- You want the newest releases and release candidates of Mesa.
- You have a modern (x86-64-v3) CPU. (If `ld.so --help` doesn't say `x86-64-v3` is supported, do not install!).
- You want additional fixes from [Open Gaming Collective](https://opengamingcollective.org/) patches.
- You don't need patented multimedia codec support.

**Choose Terra's mesa builds if**:
- You want the newest releases of Mesa, but not release candidates.
- You want full multimedia codec support.
- You want additional fixes from [Open Gaming Collective](https://opengamingcollective.org/) patches.
- I primarily use Terra's mesa builds. And I switch to this repo temporarily when I want release candidates. Find terra-mesa installation instructions below.

**Choose [xxmitsu/mesa-git](https://copr.fedorainfracloud.org/coprs/xxmitsu/mesa-git/) if**:
- You want the newest features and optimizations before they're released.
- You can accept possible regressions and instability.
- You don't need patented multimedia codec support.

**Choose stock Fedora packages if**:
- You want to maximize stability.
- You like that updates are reviewed by Fedora community testers before you get them.
- You don't need small performance gains from newer versions.
- You don't need patented multimedia codec support.

#### Installation Instructions

Installing is easy:
```bash
sudo dnf copr enable adil192/mesa-x86-64-v3
sudo dnf update mesa* --allow-vendor-change
reboot
```

#### Uninstall instructions

##### Temporarily

You can temporarily revert to Fedora's stable packages with this command.
```bash
sudo dnf --disablerepo=copr:copr.fedorainfracloud.org:adil192:mesa-x86-64-v3* distro-sync
```

The next time you update your packages, mesa-x86-64-v3 will be reinstalled.

##### Permanently

Or permanently go back to Fedora's stable packages:
```bash
sudo dnf copr remove adil192/mesa-x86-64-v3
sudo dnf distro-sync
```

#### Alternative: terra-mesa

If you don't need release candidates,
go for [Terra](https://terrapkg.com/)'s mesa builds.
They come with full multimedia codec support that we can't provide on COPR due to patent restrictions.

```bash
sudo dnf install --nogpgcheck --repofrompath 'terra,https://repos.fyralabs.com/terra$releasever' terra-release
sudo dnf install terra-release-mesa
sudo dnf update --refresh --allow-vendor-change
```

#### Development

This repo is forked from Fedora's official mesa package sources.

If you want to clone this repo to contribute, run this:
```
git clone https://github.com/adil192/mesa.git
cd mesa
git remote add upstream https://src.fedoraproject.org/rpms/mesa.git
git fetch upstream main
```

I regularly rebase this repo from upstream so expect force pushes.
