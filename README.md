# Installing FFmpeg in an n8n Docker Container

## Prerequisites
- Docker installed and running on your system
- Container name or ID of your running n8n instance
- Root access or permissions to execute Docker commands

## Step-by-Step Instructions

### Step 1: Access the Running n8n Container
```bash
docker exec -u 0 -it <container_name_or_id> /bin/sh
```
> **Note:** Replace `<container_name_or_id>` with the name or ID of your running n8n container.

### Step 2: Update Package Manager
```bash
apk update
```

### Step 3: Install FFmpeg
```bash
apk add --no-cache ffmpeg
```

### Step 4: Verify FFmpeg Installation
```bash
ffmpeg -version
```
> **Tip:** This command will display the installed version of ffmpeg if the installation is successful.

### Step 5: Commit Changes (Optional)
1. Exit the container:
```bash
exit
```

2. Commit the changes:
```bash
docker commit <container_name_or_id> n8n-with-ffmpeg
```
> **Note:** Use the new image (`n8n-with-ffmpeg`) in your future deployments.

## Common Issues and Troubleshooting

### 1. Permission Errors
- Ensure you are running the container as the root user by using the `-u 0` flag in the `docker exec` command.

### 2. Package Not Found
If `apk add ffmpeg` fails, try the following:

1. Add repositories to `/etc/apk/repositories`:
```
https://dl-cdn.alpinelinux.org/alpine/v3.20/main
https://dl-cdn.alpinelinux.org/alpine/v3.20/community
```

2. Update packages:
```bash
apk update
```

## Testing FFmpeg in n8n

1. Add a Terminal node in your n8n workflow.
2. Execute a simple ffmpeg command:
```bash
ffmpeg -version
```
3. Confirm that the output shows the correct ffmpeg version.

## Additional Resources
- Docker Documentation: https://docs.docker.com/
- n8n Documentation: https://docs.n8n.io/
- FFmpeg Official Website: https://ffmpeg.org/

## Troubleshooting Contact
If you encounter persistent issues, consult:
- Docker Community Forums
- n8n Community Support
- FFmpeg Discussion Groups

## Version Information
- Guide Last Updated: November 2024
- Recommended Alpine Linux Version: v3.20
- Compatibility: n8n Docker Containers
