Fedora container action
=======================


Run commands in a Fedora container environment


## Usage

```yaml
      - name: Build project
        uses: gbraad-actions/fedora-action@main
        with:
          script-file: './build.sh'
          dnf-packages: 'gcc make cmake'
```

```yaml
      - name: Package artifacts
        uses: gbraad-actions/fedora-action@main
        with:
          run: |
            dnf install -y rpm-build
            ./scripts/package.sh
```



> [!NOTE]
> If more complex steps are necessary, considering using something like:
> ```yaml
>     container:
>       image: ghcr.io/gbraad-actions/fedora:stable
>       options: --privileged
>     steps:
>       - uses: actions/checkout@v4
>       - run: dnf install -y gcc make cmake && ./build.sh
>       - run: dnf install -y rpm-build && ./scripts/package.sh
> ```
> In this caase you can continue with the state of the container, as this action restarts this cleanly for each step.

