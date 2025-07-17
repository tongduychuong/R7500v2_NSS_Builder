# ipq806x Builder

This project automates the process of building OpenWrt firmware images for the Qualcomm IPQ806x platform, specifically targeting the Netgear R7500v2 router. The build process incorporates various optimizations, hardening options, and quality-of-life enhancements. 

## Features

- Automated build process triggered by new commits in the [remote repository](https://github.com/tongduychuong/R7800-nss) or manual workflow dispatch
- Compiler optimizations for improved performance
- Hardening build options for enhanced security
- SSH configuration with strong algorithms and key exchange methods. Refer to the [`ssh_hardening.config`](files/etc/ssh/sshd_config.d/ssh_hardening.conf)
- Additional useful packages. Refer to the [`r7500v2.config`](r7500v2.config)
- Full NSS (Network Subsystem) support 
- Quality-of-life enhancements through UCI configuration

## Build Process

The build process is automated using GitHub Actions and consists of the following steps:

1. Check for new commits in the [remote repository](https://github.com/tongduychuong/R7800-nss)
2. Install the necessary dependencies
3. Checkout the [remote repository](https://github.com/tongduychuong/R7800-nss) and the current repository
4. Update and install the OpenWrt feeds
5. Configure the firmware image using the provided configuration file
6. Include SSH hardening configuration and QOL-Enhancements
7. Build the firmware image
8. Package the output and upload the artifacts
9. Create a new release with the updated prebuilt images

## Configuration

The project utilizes a custom configuration file [`r7500v2.config`](r7500v2.config) to specify the desired settings for the firmware build. This file includes various options such as target platform, compiler optimizations, package selections, and more.

Additionally, the `uci` commands in the "Quality-of-Life Enhancements" section are used to fine-tune the wireless and network settings for improved performance and functionality. Refer to the [999-QOL_config](https://github.com/tongduychuong/R7500v2_NSS_Builder-main//blob/main/files/etc/uci-defaults/999-QOL_config) for the specific configuration. 

## SSH Hardening

To enhance the security of SSH connections, the project includes a hardened SSH configuration. The configuration is derived from recommendations by [SSH-Audit](https://github.com/jtesta/ssh-audit) and the [BSI](https://www.bsi.bund.de/), it specifies strong key exchange algorithms, ciphers, message authentication codes (MACs), host key algorithms, and public key algorithms. This ensures that only secure and up-to-date algorithms are used for SSH communication.


## Contributing

Contributions to this project are welcome. If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request on the GitHub repository.

## Acknowledgements

- The OpenWrt project for providing the foundation for this firmware build.
- The Qualcomm IPQ806x platform and the R7500v2 router for the hardware support.
- The community over at the [OpenWrt forum](https://forum.openwrt.org/t/ipq806x-nss-build-netgear-r7800-tp-link-c2600-linksys-ea8500/82525) for their valuable contributions and resources. 
- And a special thanks to [asvio](https://github.com/asvio/R7800-nss/tree/r7800-k6.x-nss) for the main NSS development
