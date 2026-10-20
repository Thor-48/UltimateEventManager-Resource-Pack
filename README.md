# UltimateEventManager resource pack

This is a resource-pack skeleton for the original Tempest Axe item. Its current model
deliberately uses Minecraft's netherite-axe texture as a placeholder; it does not include
third-party movie-derived textures or models.

## Build and host

Run `gradle resourcePackZip` in the plugin project. The archive is written to
`build/distributions/ultimate-event-manager-resource-pack.zip` and has `pack.mcmeta` at
the ZIP root. The published archive is available from the
[public resource-pack repository](https://github.com/Thor-48/UltimateEventManager-Resource-Pack).
Use its direct raw-file or release download URL, not the repository HTML page.

Copy the archive's SHA-1 hash into `resource-pack.sha1` in the plugin configuration. Set
the matching `resource-pack.local-url` or `resource-pack.remote-url` to the direct URL.
The plugin configuration defaults to the published HTTPS ZIP, but resource-pack delivery
is opt-in and must be enabled in the configuration or admin menu.

## Adding a model you are allowed to use

1. In Blockbench, create or import a Java item model and export it as a Minecraft Java
   **Item model** (`.json`). Check the model's usage license before putting it on a server.
2. Put the exported model at `assets/uem/models/item/tempest_axe.json`, replacing the
   placeholder. Put its PNG texture(s) under `assets/uem/textures/item/` and update the
   texture paths in the model JSON (for example, `uem:item/tempest_axe`).
3. Keep the custom-model-data mapping in `assets/minecraft/items/netherite_axe.json`.
   The plugin assigns custom model data value `1` to the Tempest Axe item.
4. Zip the **contents** of this `resource-pack` directory so that `pack.mcmeta` is at the
   root of the ZIP. Host that ZIP at a direct HTTP(S) download URL.
5. Set `resource-pack.enabled: true` in `plugins/UltimateEventManager/config.yml`, then
   choose `resource-pack.mode: LOCAL` or `REMOTE` and set the matching URL and SHA-1 hash.
   Use `/uem reload`.

`LOCAL` is only useful when every connecting client can reach the URL configured in
`local-url`. In particular, `localhost` points to each player's own computer, not to the
Minecraft server. For a public server, use a publicly reachable HTTPS URL in `remote-url`.
This plugin does not host the ZIP or create a web server for it.

The pack prompt is optional. If you decline it, you are not kicked by this plugin; use
`/uem pack` to request the prompt again.

See [LICENSE.txt](./LICENSE.txt) for restrictions on original UltimateEventManager
resource-pack files. The placeholder vanilla texture remains Minecraft-owned and is not
relicensed by that file.
