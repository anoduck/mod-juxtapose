# Hinode Module - Template

<!-- Tagline -->
<p align="center">
    <b>A template to define a Hugo module compatible with Hinode</b>
    <br />
</p>

<!-- Badges -->
<p align="center">
    <a href="https://gohugo.io" alt="Hugo website">
        <img src="https://img.shields.io/badge/generator-hugo-brightgreen">
    </a>
    <a href="https://gethinode.com" alt="Hinode theme">
        <img src="https://img.shields.io/badge/theme-hinode-blue">
    </a>
    <a href="https://github.com/anoduck/mod-juxtapose/commits/main" alt="Last commit">
        <img src="https://img.shields.io/github/last-commit/anoduck/mod-juxtapose.svg">
    </a>
    <a href="https://github.com/anoduck/mod-juxtapose/issues" alt="Issues">
        <img src="https://img.shields.io/github/issues/anoduck/mod-juxtapose.svg">
    </a>
    <a href="https://github.com/anoduck/mod-juxtapose/pulls" alt="Pulls">
        <img src="https://img.shields.io/github/issues-pr-raw/anoduck/mod-juxtapose.svg">
    </a>
    <a href="https://github.com/anoduck/mod-juxtapose/blob/main/LICENSE" alt="License">
        <img src="https://img.shields.io/github/license/anoduck/mod-juxtapose">
    </a>
</p>

## About

![Logo](https://raw.githubusercontent.com/gethinode/hinode/main/static/img/logo.png)

Hinode is a clean blog theme for [Hugo][hugo], an open-source static site generator. Hinode is available as a
[template][repository_template], and a [main theme][repository]. <!-- This repository maintains a Hugo module to add
[module][module] to a Hinode site. --> Visit the Hinode documentation site for [installation instructions][hinode_docs]. 

## Contributing

This module uses [semantic-release][semantic-release] to automate the release of new versions. The package uses `husky`
and `commitlint` to ensure commit messages adhere to the [Conventional Commits][conventionalcommits] specification. You
can run `npx git-cz` from the terminal to help prepare the commit message.

## Configuration

This module takes no parameters in `config.toml`, rather, it's configuration and data are contained within a yaml file
located in the `data` directory. The current configuration of the module **REQUIRES** this file to be named
`juxtapose.yml`. Furthermore, the module is structured to only allow one juxtapose element per site. Please see note
immediately below.

>[!NOTE]
> If any user desires to have more than one juxtapose element in their site or even per page, this will require
> restructuring the module to enable this configuration. So, please submit a feature request.

The following are keywords used in the creation of a valid yaml file for juxtapose.

| Keywords         | Description                                                             | Required | Type       |
|------------------|-------------------------------------------------------------------------|----------|------------|
| Frames           | Structural: Indicates the beginning of an two part image object array   | Yes      | Stuctural  |
| image            | Structural: Indicates the beginning of a description of an image object | Yes      | Structural |
| src              | The src url of the image for the juxtapose element                      | Yes      | Data       |
| label            | The label for the juxtapose image.                                      | No       | Meta       |
| credit           | Credit to provide for the juxtapose image.                              | No       | Meta       |
| animate          | Whether to display animations                                           | No       | Boolean    |
| showLabels       | Whether to display Labels                                               | No       | Boolean    |
| showCredits      | Whether to display credits.                                             | No       | Boolean    |
| startingPosition | Where should the slider start?                                          | No       | Setting    |
| makeResponsive   | Whether the juxtapose element should be responsive or not?              | No       | Setting    |

A well stuctured juxtapose yaml file will look like below.

```yaml
frames:
    - image:
        src: "https://some.example.site/assets/images/some.image"
        label: "Look Ma! A label."
        credit: "No thanks, I prefer cash."
    - image:
        src: "https://some.example.site/assets/images/another.image"
        label: "Look Ma! Another label."
        credit: "Sure, why not?"
animate: True
showLabels: True
showCredits: True
startingPosition: "50%"
makeResponsive: True
```

A json schema file has been created to aid in this process.

## Usage

Usage of this module is embodied through the employment of a shortcode and the aforementioned yaml file. The shortcode
merely consists of the tag "juxtapose". The remainder configuration belongs in the yaml file.

```markdown
{{< juxtapose >}}
```

And your all set to have the juxtapose element in your Hinode site.

---

<!-- MARKDOWN LINKS -->
[hugo]: https://gohugo.io
[hinode_docs]: https://gethinode.com
<!-- [module]: https://example.com -->
[repository]: https://github.com/gethinode/hinode.git
[repository_template]: https://github.com/gethinode/template.git
[conventionalcommits]: https://www.conventionalcommits.org
[husky]: https://typicode.github.io/husky/
[semantic-release]: https://semantic-release.gitbook.io/
