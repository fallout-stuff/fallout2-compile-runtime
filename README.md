# Fallout2 Compile Runtime

This repository contains a GitHub Action that builds the Fallout2 runtime environment by:

1. Cloning the Fallout2 Restoration Project repository
2. Cloning the sfall repository
3. Extracting necessary headers and scripts
4. Extracting runtime binaries from the included zip file

## Structure

After the build process, the repository will contain:

- `headers/` - Header files from Fallout2 Restoration Project and sfall
- `scripts/` - Script source files from Fallout2 Restoration Project
- `bin/` - Runtime binaries extracted from the zip file

## GitHub Action

The GitHub Action (`/.github/workflows/build.yml`) automatically:

- Triggers on pushes to main/master branches and pull requests
- Can be manually triggered via workflow_dispatch
- Clones required repositories
- Moves and organizes files
- Extracts binaries
- Uploads the final artifacts
- Creates a GitHub release with the latest tag (if it doesn't already exist)

## Manual Build

To build locally, you can run the equivalent commands:

```bash
# Clean up existing directories
rm -rf ./headers ./scripts ./bin

# Clone repositories
git clone https://github.com/BGforgeNet/Fallout2_Restoration_Project.git
git clone https://github.com/sfall-team/sfall.git

# Move files
mv Fallout2_Restoration_Project/scripts_src/headers ./headers
mv Fallout2_Restoration_Project/scripts_src ./scripts
mv sfall/artifacts/scripting/headers ./headers/sfall

# Clean up
rm -rf Fallout2_Restoration_Project sfall

# Extract binaries
mkdir -p ./bin
unzip fallout2-runtime-binaries.zip -d ./bin/
```

## Dependencies

- Git (for cloning repositories)
- Unzip (for extracting binaries)
- Access to the specified GitHub repositories
