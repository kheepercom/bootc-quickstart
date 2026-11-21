# bootc-quickstart

Examples for quickly provisioning servers with bootc.

## fedora-bootc

A Fedora bootc image with an `admin` user you can SSH in as.

1. Fork this repo.
2. Replace the key in `fedora-bootc/tmpfiles_admin_authorized_keys` with your public key.
3. Push to `main`. GitHub Actions builds and pushes `ghcr.io/<you>/bootc-quickstart/fedora-bootc:main`.
4. Make the package public: Packages → `bootc-quickstart/fedora-bootc` → Package settings → Change visibility.
5. Launch an instance with the [quickstart image](https://kheeper.com/bootc-quickstart). On GCP:

   ```sh
   gcloud compute instances create fedora-bootc-quickstart \
     --image-project kheeper --image-family bootc-quickstart \
     --machine-type c4-standard-2 \
     --boot-disk-size 20GB \
     --metadata 'bootc-image=ghcr.io/<you>/bootc-quickstart/fedora-bootc:main'
   ```

   On first boot it switches to your image and reboots. Follow along with `gcloud compute instances tail-serial-port-output fedora-bootc-quickstart`.

6. `ssh admin@<instance-ip>`
