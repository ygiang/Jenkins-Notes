# Using multiple kubernete KubeConfig file
1. Make sure that `git` is installed.
2. Run this command in your terminal to download and install `krew`:

    ```sh
    (
      set -x; cd "$(mktemp -d)" &&
      curl -fsSLO "https://github.com/kubernetes-sigs/krew/releases/download/v0.3.3/krew.{tar.gz,yaml}" &&
      tar zxvf krew.tar.gz &&
      KREW=./krew-"$(uname | tr '[:upper:]' '[:lower:]')_amd64" &&
      "$KREW" install --manifest=krew.yaml --archive=krew.tar.gz &&
      "$KREW" update
    )
    ```
3. Add `$HOME/.krew/bin` directory to your PATH environment variable. To do
   this, update your `.bashrc` or `.zshrc` file and append the following line:

     ```sh
     export PATH="${KREW_ROOT:-$HOME/.krew}/bin:$PATH"
     ```

   and restart your shell.

4. kubectl krew search konfig
5. kubectl krew install konfig
6. Import in KubeConfig file
    ```sh
    kubectl konfig import -s jean-grey.kconfig
    ```
#### Getting a list of kubernetes clusters from your Kubeconfig profile
```sh
kubectl config get-clusters
```
#### Change to a another kubernete cluster in your Kubeconfig profile
```sh
kubectl config use-context jean-grey
```