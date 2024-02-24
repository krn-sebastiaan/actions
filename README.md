# Actions for working with mMojos

This repository holds several GitHub Actions to make your life easier regarding the lifecycle of mMojos.

# compile

## Options

```yaml
  krn-core-version:
    default: 0.4.0+20240221-0755
    required: false
    type: string
  build-xml-path:
    default: build.xml
    required: false
    type: string
  build-arguments:
    default: ''
    required: false
    type: string
  mmojo-name:
    default: ${{ github.event.repository.name }}
    required: false
    type: string
  krn-core-repository-url:
    default: ''
    required: false
    type: string
  gpg-passphrase:
    required: true
    type: string
```

## Example configuration

```yaml
name: Compile mMojo

on:
  push:
    branches:
      - "**"
  pull_request:
    branches:
      - "**"

jobs:
  compile:
    runs-on: ubuntu-latest
    steps:
      - name: Compile mMojo
        uses: krn-sebastiaan/actions/compile@main
        with:
          gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
```

# release

## Options

```yaml
  krn-core-version:
    default: 0.4.0+20240221-0755
    required: false
    type: string
  build-xml-path:
    default: build.xml
    required: false
    type: string
  build-arguments:
    default: ''
    required: false
    type: string
  mmojo-name:
    default: ${{ github.event.repository.name }}
    required: false
    type: string
  krn-core-repository-url:
    default: ''
    required: false
    type: string
  gpg-passphrase:
    required: true
    type: string
```

## Example configuration

```yaml
name: Release mMojo

on:
  push:
    tags:
      - '*.*.*'

jobs:
  release:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - name: Release mMojo
        uses: krn-sebastiaan/actions/release@main
        with:
          gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
```

# krn-core

See [krn-sebastiaan/krn-core](https://github.com/krn-sebastiaan/krn-core)
