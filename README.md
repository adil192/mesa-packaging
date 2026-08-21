# [mesa-rc](https://copr.fedorainfracloud.org/coprs/adil192/mesa-rc/)

Almost-stable releases of mesa3d graphics drivers: get the newest features with the fewest bugs.

This repo is an alternative to `mesa-git` copr repos.
Instead of the bleeding edge git versions, we stick to releases and release candidates from the Mesa team.
This somewhat shields against instability from unreleased mesa versions.

Use at your own risk!

This COPR's packages:
- are based on the official Fedora mesa repo.
- use [Open Gaming Collective](https://opengamingcollective.org/) patches.
- enable the AMD Anti-lag vulkan layer.
- are easily auditable: there are only a few small commits on top of Fedora's repo: see [https://github.com/adil192/mesa](https://github.com/adil192/mesa).
- are automatically updated at most 2 days after being tagged upstream.

#### Install

Enable this copr repo, update your packages, and reboot:
```bash
sudo dnf copr enable adil192/mesa-rc
sudo dnf update --refresh
reboot
```

#### Uninstall

You can temporarily revert to Fedora's stable packages with this command. The next time you update your packages, mesa-rc will be reinstalled.
```bash
sudo dnf --disablerepo=copr:copr.fedorainfracloud.org:adil192:mesa-rc* distro-sync
```

Or permanently go back to Fedora's stable packages:
```bash
sudo dnf copr remove adil192/mesa-rc
sudo dnf distro-sync
```

#### Alternatives

If you're okay with the slightly slower release cadence (i.e. no release candidates),
go for [Terra](https://terrapkg.com/)'s mesa builds.
They come with full multimedia codec support that we can't provide on COPR due to patent restrictions.

```bash
sudo dnf install --nogpgcheck --repofrompath 'terra,https://repos.fyralabs.com/terra$releasever' terra-release
sudo dnf install terra-release-mesa
sudo dnf update --refresh
```

You *could* use RPM Fusion's mesa-freeworld packages instead of Terra's,
but I recommend Terra's since they include Open Gaming Collective patches
and enable more Mesa features.

#### Cloning

This repo is forked from Fedora's official mesa package sources.

If you want to clone this repo to contribute, run this:
```
git clone https://github.com/adil192/mesa.git
cd mesa
git remote add upstream https://src.fedoraproject.org/rpms/mesa.git
git fetch upstream main
```

I regularly rebase this repo from upstream so expect force pushes.
