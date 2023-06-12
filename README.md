# DayZ-Legacy-Launcher

A launcher and updater tool for the DayZ Legacy client.

Derived from the open-source CPPGameLauncher. https://github.com/FLWL/CPPGameLauncher

# Features
- Download game files over HTTP 
- Verify the origin of files using RSA key
- Verify the integrity of downloaded files using SHA-256 hashes
- Determine which files need to be updated by comparing CRC hashes and file sizes 
- Support multiple remote servers
- Launcher can update itself
- Repair installation function
- Show news in launcher
- About page
- Keep track of installed files in .ini file for uninstallers
- Choose game renderer (DX9, DX11, DXVK)
- Choose game platform (x86-64)
- Choose game display mode (windowed vs fullscreen)
- Choose game memory allocator
- Choose game map
- Disable/enable game logs
- Disable/enable game console
- Disable/enable low-end and developer modes
- Run program as administrator
- Debug and utility functions to reset the user's game configuration, pack debug logs, cleanup un-needed files, clean the Vulkan cache and more
- Change default in-game name
- Button to join Discord for additional support

# Launcher Guide

When you first start the launcher you will be prompted to configure your game settings. Here is a detailed explanation of what each setting does, and the recommended configuration.

- Game Platform: Select between DirectX 9, DirectX 11, and Vulkan. (recommended selection: DirectX 11)
    - DirectX 9:
        - The default vanilla renderer from pre-alpha DayZ.
        - Very, very slow performance. Abysmal framerates.
        - Most visually accurate to pre-alpha DayZ in terms of lighting, shading, and object/UI rendering.
        - Great compatibility with a massive range of hardware. DirectX 9 runs on almost any GPU made within the last 15 years.
        - This build is not recommended for use at all and is only provided as a fallback in case of hardware incompatibility.
    - DirectX 11:
        - Our custom renderer solution for DayZ Legacy.
        - Performs up to 80% better than the DirectX 9 client and has a much higher average FPS value.
        - Built with higher-end machines in mind, better hardware utilization.
        - You may notice small or large changes in lighting, shading, or object/UI rendering and potentially exclusive issues like artifacting, visual inconsistencies, or crashes. 
        - Seriously, can't stress enough how much better this renderer is in terms of performance. 
        - This build is recommended for all users by the DayZ Legacy team and is set as the current default.
        - Good support for a wide range of hardware.
        - The requirements for DirectX 11 are as follows:
            - NVIDIA: Fermi-series GPU (GTX 470) or later required. 
            - AMD: Radeon HD 5450 or later required.
            - Intel: Intel HD Graphics 4000 or later required.
    - Vulkan (DXVK): 
        - A "best-of-both-worlds" solution between DirectX 9 and DirectX 11.
        - Performs up to 60% better than the DirectX 9 client and has a higher average FPS value.
        - Uses the DXVK translation layer to render the default Direct3D 9 scene on top of a Vulkan device. More info: https://github.com/doitsujin/dxvk
        - Maintains the same visuals as DirectX 9.
        - May have very small and minor visual inconsistencies.
        - Not compatible with older hardware and GPUs.
        - This build is recommended if you are okay with a slightly lower framerate in exchange for more accurate visuals.
        - According to sources from Khronos, NVIDIA, and AMD, the requirements for Vulkan are as follows:
            - NVIDIA: Kepler (600-series) GPU or later required. The GTX 750 and 750 Ti are not supported.
            - AMD: Radeon HD 7000 series or later required.
            - Intel: Skylake CPU or later required. You must be running driver version 15.45.14.4590 or later.

- Game Platform: Select between 32-bit and 64-bit. (recommended selection: 32-bit)
    - 32-bit: 
        - This was the default client provided until pre-alpha 0.62.
        - The most stable platform for DayZ Legacy.
        - Subject to standard 32-bit memory and performance limitations.
        - This build is "Large Address Aware", meaning the engine can use up to 4GB of RAM, v.s. the default 2GB.
        - This platform is recommended for all users by the DayZ Legacy Dev team and is set as the current default.
        - Caveat: You'll still be stuck at 2GB if your system is 32-bit, but any processor made in the past 15 years is going to be 64-bit, so this is a very rare situation.
    - 64-bit:
        - An enhanced, custom-developed client from the DayZ Legacy Dev team.
        - A more unstable platform with limited performance advantages.
        - Can improve performance and loading times in specific situations
        - This build has many crashes, instability, and performance issues we are actively investigating and fixing.
        - Your mileage may vary on this platform and nothing is guaranteed.

- Display Mode: Select between Windowed and Fullscreen (Exclusive) (recommended selection: Fullscreen (Exclusive))
    - Windowed: 
        - The game runs in a resizable window. Better for multi-monitor users until proper multi-monitor support is added. This can sometimes mess up your graphics settings.
        - Caveat: Moving from windowed mode to fullscreen or vice versa may crash the game.
    - Fullscreen (Exclusive):
        - The game runs in an exclusive full-screen window. Better for single monitor users.

- Memory Allocator: Select between System and Community Memory Allocator (recommended selection: System)
    - System:   
        - Allows the OS to manage the game's memory. 
        - Good compatibility and performance.
    - Community Memory Allocator: 
        - An open-source memory allocator used primarily in ARMA 3 to increase performance. 
        - Also known as xtbbmallloc. 
        - Can sometimes increase performance and reduce memory usage.
        - Your mileage may vary and your experience will be highly subjective. 

- Game Map
    - Not currently supported.

- Pack Debug Logs
    - Creates a compressed archive of the `logs` folder in your main game directory. 
    - A ZIP file called `bug_report` with a timestamp will be created in the main game directory.
    - Use this function to pack your logs, and then send them to us via the #bug-report channel on Discord.
- Restart Steam
    - Closes any running instances of Steam.
    - Should only be used if you are having issues with Steam when launching the game.
    - Relaunch Steam, and then try to open the game again after using this option.
- Reset Vulkan cache
    - Deletes all Vulkan cache files.
    - Can sometimes resolve crashes or performance issues in DayZ Legacy Vulkan builds.
    - Should ONLY be used if you are regularly playing with the DayZ Legacy Vulkan build.
    - This will force a re-generartion of the shader cache, which will cause stutters and various performance issues for up to an hour of gameplay.
- Reset Game Configuration
    - Deletes all DayZ Legacy config files.
    - Completely resets all settings for the game, including graphics, volume, controls etc
    - Can fix some various minor issues
    - Caveat: You will need to re-configure all game settings to your liking and then save the settings by restarting the game. 
- Cleanup Install
    - Cleans any files that aren't supposed to be in your game directory.
    - Resolves issues with "Bad version: Server rejected connection" when trying to join.
    - Resolves "red dot" and "red X" issues when trying to join.
    - Should only be used as an emergency measure.
    - Caveat: Can potentially delete files that you did not intend to delete.
- *DANGER* Re-install
    - Deletes all files from the game directory and starts downloading a fresh copy. 
    - Should ONLY be used when directed by a DayZ Legacy developer.
    - Will require at least a 15GB download.
    - This should only be done if all else fails.
- Change Name
    - Sets your default Survivor name.
    - Recommended that you set your name using this tool before joining the server for the first time.

- Disable Logs
    - Stops log files from being written.
    - 99.9% of the time, we don't need this. Log files are required by the devs for debugging.
- Disable Debug Console
    - Stops the debug console from being opened.
    - Moves all relevant logs to the game.log file sink instead.
    - Useful for "extended logging sessions"
    - Should not be enabled unless a DayZ Legacy developer requests you to.
- Boot in Debug Mode
    - This function is disabled for anybody who isn't registered as a DayZ Legacy developer and is therefore irrelevant.
- Boot in Low-End Mode
    - Boots the game in a special "low-end" mode
    - Designed for ancient or very low-spec PCs
    - Disables many graphic options and post-processing effects
    - Moves texture quality to an incredibly low level
    - Limits view distance to reduce scene complexity
    - Creates global fog which will improve performance
    - Recommended for any users operating on budget hardware or any hardware older than 10 years
    - Caveat: Puts character at a disadvantage in player combat scenarios

- Join our Discord!
    - If you're not already a part of our Discord, this is a great way to get additional support for issues.