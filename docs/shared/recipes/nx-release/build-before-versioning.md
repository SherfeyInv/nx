# Build Before Versioning

In order to ensure that projects are built before the new version is applied to their package manifest, you can use the `preVersionCommand` property in `nx.json`:

```json {% fileName="nx.json" %}
{
  "release": {
    "version": {
      "preVersionCommand": "npx nx run-many -t build"
    }
  }
}
```

This command will run the `build` target for all projects before the version step of Nx Release. Any command can be specified, including non-nx commands. This step is often required when [publishing from a custom dist directory](/recipes/nx-release/publish-custom-dist-directory), as the dist directory must be built before the version is applied to the dist directory's package manifest.
