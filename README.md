# CHANGELOG.md

Chronological ordered list of **notable changes** for each software version

## Be useful to readers

A Changelog keep additions and changes legible and organized for:

1. **Developpers**, consuming software via dependencies
2. **Maintainers** and **contributors**

![changelog motherfucker](https://cdn.meme.am/instances/59893394.jpg)

## Prioritize information

Mostly read by developers & maintainers, usually curated to create *release notes*

* Dependency (public API) ⇨ outline **Breaking changes** between versions
* Product ⇨ list new and improved **Features** between releases

![ch ch ch ch changes](https://southinpopculture.files.wordpress.com/2016/05/changes.png?w=440)

## Notify consumers

People look for reasons to upgrade like

**bug** fix, **security** patch and best **performance**

### Changes and removal need to be highlighted

![keep calm](http://www.lexibites.com/wp-content/uploads/2014/11/keep-calm-changes-are-coming-5.png)

## Semver to the rescue!

Software with public API MUST use [Semver]
- Vital for dependency management
- Simple signal: **major**.*minor*.patch = **breaking**.*feature*.fixed

Use 0.y.z for initial development, before API is public

![semver all the thing](https://ez.no/var/ezflow_site/storage/images/media/images/image01/528970-1-eng-GB/image01.png)

## Old Standards

**1980** [GNU] NEWS file standard

**1995** [Debian] package changelog policy

**2010** [Perl] changes files specifications

![yet another standard](https://imgs.xkcd.com/comics/standards.png)

## Keep a changelog

**2014** [keepachangelog.com], a modern CHANGELOG file convention

- Structures information using simple **text & hyperlink**, using [Markdown]
- Offers practical convention & clear **guidelines**
- Defines **groups** to describe impacts on the project:
	- `Deprecated` features removed in upcoming releases
	- `Removed` deprecated features removed in this release
	- `Changed` changes in existing functionality
	- `Added` new features
	- `Fixed` any bug fixes
	- `Security` invite users to upgrade in case of vulnerabilities

*See* [CHANGELOG.md](https://github.com/olivierlacan/keep-a-changelog/blob/master/CHANGELOG.md)

## Good changelog

1. **Visibility** easily available = repository root, first link of README
2. **Readability** released version with legible date
3. **Accuracy** stay clear and up to date

#### Git log is not a changelog

![git commit messages](https://imgs.xkcd.com/comics/git_commit.png)

*Tip* 7 rules to write good [git commit]

## Maintaining

Manually maintaining a changelog is painful

- **Not easy** to integrate in release cycle
- Too often a **burden** for a single developper 

*Changelog updates should be part of merge requests*

![made by hand](http://www.addamsfamily.com/addams/afthing1.jpg)

*Tip* use .gitattributes to [avoid merge conflict] `CHANGELOG.md merge=union`

## v.s. Automatic generation

Generate a changelog from git metadata is preferable to maintaining it manually

- Use existing tool, **do not spend time** formating / organizing information
- **Think about changes** and document it as part of the modification
- Automated changelog generation can be **done by CI server**
- **Stop messing with semver**, version bump from git commit messages

![automation is giant](http://i.kinja-img.com/gawker-media/image/upload/t_original/jjp5g6r0pa8i4q5wian8.png)

## Git commit message convention 

Choose a **git commit message convention** (angular, jquery, atom, eslint)

```
git commit -a -m "feat(parser): introduce a new parsing library
BREAKING CHANGE: new library does not support foo-construct"
```

And a **tool to automate changelog generation**

Ex: [conventional-changelog-cli], [standard-version], [semantic-release], etc.

![js tools](https://www.allenpike.com/images/2015/javascript-guy.jpg)

## Release cycle

Automation is useful when fully **intergrated in release cycle**

- **Review changelog** messages as carefully as code
- Generate changelog on **merge and tag**
- Enforce convention with **[message templates] or linting**

![release cycle](http://a69.g.akamai.net/n/69/10688/v1/img5.allocine.fr/acmedia/medias/nmedia/18/35/07/94/p6.jpg)

## Git notes alternative

[harrow.io] promotes the use of [git notes] to automate changelog generation

- Can be added / edited after git commits *without changing hashes*
- Allow to *group notes* by type (deprecated, removed, changed, ...)
- *Integrated with git* commands like git log, alias, etc.

Still, there is yet very [little tooling] using git notes


[Semver]: http://semver.org

[GNU]: https://www.gnu.org/prep/standards/standards.html#NEWS-File
[Debian]: https://www.debian.org/doc/debian-policy/ch-source.html#s-dpkgchangelog
[Perl]: https://metacpan.org/pod/distribution/CPAN-Changes/lib/CPAN/Changes/Spec.pod

[keepachangelog.com]: http://keepachangelog.com/en/0.3.0
[Markdown]: https://daringfireball.net/projects/markdown

[git commit]: http://chris.beams.io/posts/git-commit

[avoid merge conflict]: https://gitlab.com/gitlab-org/gitlab-ce/commit/d899bc914f07ce47b5962563467790c25ba52c89

[conventional-changelog-cli]: https://github.com/stevemao/conventional-changelog-cli
[standard-version]: https://www.npmjs.com/package/standard-version
[semantic-release]: https://www.npmjs.com/package/semantic-release

[message templates]: https://gitlab.com/help/customization/issue_and_merge_request_template.md

[harrow.io]: https://harrow.io/blog/effortlessly-maintain-a-high-quality-change-log-with-little-known-git-tricks
[git notes]: https://git-scm.com/docs/git-notes
[little tooling]: https://github.com/harrowio/notes-example/blob/master/scripts/changelog
