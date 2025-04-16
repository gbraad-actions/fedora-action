Fedora container action
=======================


Run commands in a Fedora container environment


## Usage

```yaml
      - name: Build project
        uses: gbraad-action/fedora-action@main
        with:
          script-file: './build.sh'
          dnf-packages: 'gcc make cmake'
```

```yaml
      - name: Package artifacts
        uses: gbraad-action/fedora-action@main
        with:
          run: |
            dnf install -y rpm-build
            ./scripts/package.sh
```

> [!NOTE]
> If more complex steps are necessary, considering using something like:
> ```
>     container:
>       image: ghcr.io/gbraad-actions/fedora:stable
>       options: --privileged
>     steps:
>       ...
> ```
