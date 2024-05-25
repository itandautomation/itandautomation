# k9s

| Social Media | Remarks |
| -- | -- |
|Youtube Video | [https://www.youtube.com/watch?v=0c3YPCa_16Y](https://www.youtube.com/watch?v=dTIUw2JHgZE&t=1s) |
|Twitter/X | [https://twitter.com/itnautomations/status/1784346966446559327](https://x.com/itnautomations/status/1784679989998223627) |


## Installation

First, you'll need to install K9s on your local machine. You can typically install it using package managers like Homebrew (for macOS) or Chocolatey (for Windows), or by downloading the binary from the GitHub releases page.

## Connecting to a Cluster

Once installed, you can launch K9s by running the k9s command in your terminal. K9s will prompt you to select a Kubernetes context (if you have multiple) and authenticate if necessary.

## Exploring Resources

After connecting, you'll see the main K9s dashboard, which displays various Kubernetes resources. You can navigate through namespaces and view resources such as pods, deployments, services, and more.

## Interacting with Resources

You can interact with resources using keyboard shortcuts. For example, pressing Enter on a resource will open a detailed view, while pressing Shift + D will delete the selected resource. Refer to the K9s documentation for a full list of shortcuts.

## Searching and Filtering

K9s allows you to search and filter resources easily. Press / to start a search, and use filters like labels or resource types to narrow down the results.

## Customization

You can customize K9s by modifying its configuration file (~/.k9s/config.yaml). This allows you to adjust settings such as default namespace, color themes, and custom keybindings.

## Help and Documentation

If you ever need assistance while using K9s, you can access the built-in help menu by pressing ?. Additionally, the K9s GitHub repository contains detailed documentation and usage examples.

Remember to exercise caution when performing operations with K9s, as actions like deleting resources are irreversible. It's a powerful tool, but it's essential to understand the implications of your actions in a Kubernetes environment.
