Install Helm Binary:
--------------------


  # Download Helm binary (Adjust the version as needed)
      curl -LO https://get.helm.sh/helm-v3.7.0-linux-amd64.tar.gz

# Extract the tarball
      tar -zxvf helm-v3.7.0-linux-amd64.tar.gz

# Move the Helm binary to /usr/local/bin
      sudo mv linux-amd64/helm /usr/bin/

# Clean up extracted files (optional)
      rm -rf linux-amd64 helm-v3.7.0-linux-amd64.tar.gz


verify helm install:
------------------

      helm version

