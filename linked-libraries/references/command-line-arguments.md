# Command Line Arguments, Creating A Static Extensions Repository, How To Create Extensions

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Command Line Arguments; Creating a Static Extensions Repository; How to Create Extensions.

## Command Line Arguments

Blender 5.1 command-line usage is `blender [args ...] [file] [args ...]`. Render options: -b / --background runs without the UI (often for headless rendering; audio is off in background mode unless you pass -setaudio Default after it); -a / --render-anim renders frames from start to end inclusive; -S / --scene <name> sets the scene to render; -f / --render-frame <frame> renders and saves one frame (use +<frame> for start-relative or -<frame> for end-relative, a comma-separated list without spaces, or a .. range between first and last inclusive); -s / --frame-start <frame> and -e / --frame-end <frame> set the start and end frames (both accept +/- relative values); -j / --frame-jump <frames> steps that many frames after each rendered one; -o / --render-output  sets the output path and filename (lead with // to render relative to the blend-file, use path templating such as {blend_name}, and use # characters as zero-padded frame-number placeholders — animation_##_test.png becomes animation_01_test.png, test-######.png becomes test-000001.png, and if the filename has no #, a #### suffix is appended, e.g. `blender -b animation.blend -o //render_ -F PNG -x 1 -a` turns //render_ into //render_#### and writes //render_0001.png); -E / --engine <engine> picks the render engine (-E help lists them); and -t / --threads <threads> sets threads [1-1024], 0 meaning the system's processor count. Cycles render options follow a double dash: --cycles-device <device> picks the device (CPU, CUDA, OPTIX, HIP, ONEAPI, METAL; append +CPU to a GPU device to use both, e.g. `blender -b file.blend -f 20 -- --cycles-device OPTIX`), and --cycles-print-stats logs render memory and time. Format options: -F / --render-format <format> sets the format (TGA, RAWTGA, JPEG, IRIS, PNG, BMP, HDR, TIFF, plus optionally compiled `OPEN_EXR`, `OPEN_EXR_MULTILAYER`, FFMPEG, CINEON, DPX, JP2, WEBP), and -x / --use-extension <bool> toggles adding the file extension. Animation playback options: -a <options> <file(s)> runs Blender as an animation player for movies and image sequences (ignored when -b is set), with playback arguments -p <sx> <sy> (open with the lower-left corner there), -m (read from disk, don't buffer), -f <fps> <fps_base> (starting FPS), -j <frame> (frame step), -s <frame> (play from), -e <frame> (play until), and -c <cache_memory> (megabytes for caching during playback; 0 disables and clamps to a fixed frame count). Window options: -w / --window-border (open bordered and non-maximized), -M / --window-maximized, -W / --window-fullscreen, -p / --window-geometry <sx> <sy> <w> <h>, -con / --start-console (open with the console window, Windows only, ignored with -b), --no-native-pixels (don't use native pixel size on high-DPI displays), --no-window-frame (no window decorations, Linux only), and --no-window-focus (open behind other windows without taking focus). Python options: -y / --enable-autoexec and -Y / --disable-autoexec (toggle automatic Python script execution; disabled is the default), -P / --python <filepath> (run a script file), --python-text <name> (run a text block), --python-expr <expression> (run an expression, which may be a full multi-line script limited only by the platform's argument length), --python-console (interactive console), --python-exit-code  (exit code 0-255 on an uncaught exception, only for command-line scripts; 0 disables), --python-use-system-env (let Python use PYTHONPATH and the user site-packages), and --addons <addon(s)> (comma-separated, no spaces, to enable in addition to defaults). Network options: --online-mode and --offline-mode override the internet-access preference. Logging options: --log <match> enables logging categories from a comma-separated argument (--log "*" for everything, --log "event" for categories starting with "event", --log "render,cycles" for both, --log "*mesh*" for any containing "mesh", --log "*,^operator" for everything except operators using a ^ prefix), --log-level <level> sets verbosity (fatal, error, warning, info, debug, trace), --log-show-memory, --log-show-source, --log-show-backtrace (debug builds only), --log-file <filepath>, and --log-list-categories (list and exit). Debug options: -d / --debug turns on debugging (enabling memory-error detection, disabling mouse grab so a debugger can be used, and keeping Python's sys.stdin), --debug-value <value> sets a debug value at startup, and --debug-events enables event-system debug messages.

More command-line debug options, each enabling extra messages or behavior: --debug-handlers (event handling); --debug-libmv (the libmv library); --debug-memory (fully guarded allocation and debugging); --debug-jobs (time-profile background jobs); --debug-python; --debug-depsgraph and its variants --debug-depsgraph-eval, --debug-depsgraph-build, --debug-depsgraph-tag, --debug-depsgraph-no-threads (single-threaded evaluation), --debug-depsgraph-time, --debug-depsgraph-pretty (colored messages), and --debug-depsgraph-uid (verify ID data-block session identifiers); --debug-ghost (Linux only); --debug-wintab; --debug-gpu (GPU debug context for OpenGL 4.3+); --debug-gpu-force-workarounds (enable workarounds and disable GPU extensions); --debug-gpu-compile-shaders (compile all static shaders to test compatibility); --debug-gpu-shader-debug-info (Vulkan only); --debug-gpu-scope-capture (capture GPU commands within a named scope); --debug-gpu-shader-source (save a named shader's compiled source, where the name may use leading/trailing "*" wildcards, written to a "Shaders" folder in the working directory); --debug-gpu-shader-no-preprocessor (skip the preprocessor pass, relying on the driver/compiler, and disable dead-code elimination); --debug-gpu-shader-no-dce (skip dead-code elimination); --debug-gpu-no-texture-pool (disable texture-pool aliasing optimizations); --debug-gpu-renderdoc (RenderDoc integration); --debug-gpu-vulkan-local-read (force Vulkan dynamic-rendering local read where supported); --debug-wm (window manager messages, all operators in search, keymap errors); --debug-xr (VR contexts, enabling the OpenXR validation layer and info prints); --debug-xr-time (VR frame render times); --debug-all; --debug-io; --debug-fpe (floating-point exceptions); --debug-exit-on-error (exit immediately on internal errors); and --debug-freestyle. Also: --disable-crash-handler, --disable-abort-handler, --verbose <verbose> (verbosity for debug messages that support it), and -q / --quiet (suppress status printing, though warnings and errors still print). GPU options: --gpu-backend (force vulkan, metal, or opengl), --gpu-vsync (on, off, or auto for adaptive sync — defaults depend on the driver, disabling helps performance testing, and auto is OpenGL-only), --gpu-compilation-subprocesses (override Max Compilation Subprocesses, OpenGL only), and --profile-gpu (CPU and GPU profiling for GPU debug groups, writing profile.json in the Trace Event Format to the working directory). Misc options: --open-last (open the most recent blend-file instead of the startup file), --app-template <template> (set the app template by directory name, "default" for none), --factory-startup (skip the user's startup.blend), --enable-event-simulate (enable bpy.types.Window.event_simulate testing), the --env-system-* flags (set `BLENDER_SYSTEM_DATAFILES`, SCRIPTS, EXTENSIONS, or PYTHON), -noaudio (force no sound), -setaudio (force a device: None, Default, SDL, OpenAL, CoreAudio, JACK, PulseAudio, WASAPI), -c / --command <command> (run a command consuming the remaining arguments, implying --background; -c help lists commands and --help after a command shows its help), -h / --help and /? (Windows only) to print help and exit, -r / --register and --register-allusers, --unregister and --unregister-allusers (register or unregister the blend-file extension, Windows and Linux only), --qos <level> (Quality of Service on hybrid CPUs, Windows only: default, high to favor performance cores, eco to use efficiency cores), -v / --version, and -- (end option processing, passing the rest unchanged, reachable via Python's sys.argv). Other options: --disable-depsgraph-on-file-load (in background mode with -b or -c, don't auto-build/evaluate ViewLayer dependency graphs on load, so scripts needing evaluated data must call e.g. depsgraph = context.evaluated_depsgraph_get(); this is temporary, as background-mode depsgraphs will eventually never be auto-generated on load), --disable-liboverride-auto-resync (skip library-override auto-resync on load, an alternative to the No Override Auto Resync debug preference), --debug-ffmpeg, and --debug-cycles. Argument parsing: arguments must be separated by whitespace, so `blender -ba test.blend` exits because -ba is unknown. Argument order: arguments run in order, so `blender --background test.blend --render-frame 1 --render-output "/tmp"` won't render to /tmp (the frame renders before the output is set) and `blender --background --render-output /tmp test.blend --render-frame 1` won't either (loading the blend-file overwrites the render output), whereas `blender --background test.blend --render-output /tmp --render-frame 1` works. Environment variables include `BLENDER_USER_RESOURCES` (replace the directory of all user files, with other `BLENDER_USER`_* variables overriding when set), `BLENDER_USER_CONFIG`, and `BLENDER_USER_SCRIPTS`.

More environment variables: `BLENDER_USER_EXTENSIONS` (user extensions directory); `BLENDER_USER_DATAFILES` (user data files such as icons and translations); `BLENDER_SYSTEM_RESOURCES` (replace the directory of all bundled resources); `BLENDER_SYSTEM_SCRIPTS` (add extra scripts); `BLENDER_SYSTEM_EXTENSIONS` (the system extensions repository); `BLENDER_SYSTEM_DATAFILES` (replace the bundled datafiles); `BLENDER_SYSTEM_PYTHON` (replace the bundled Python libraries); `BLENDER_CUSTOM_SPLASH` (full path to a replacement splash image); `BLENDER_CUSTOM_SPLASH_BANNER` (full path to an image overlaid on the splash); `BLENDER_OCIO` (override the OpenColorIO config file; otherwise the OCIO variable is used); `SPNAV_SOCKET` (the socket path for the 3D-mouse daemon, Unix only); TEMP (where to store temporary files on MS-Windows); and TMPDIR (where to store them on UNIX, which must reference an existing directory or it's ignored).

## Creating a Static Extensions Repository

To host your own extensions and use Blender's update system, you only need to host a static JSON file that Blender itself generates. JSON: produce a valid one with the server-generate command-line tool, `blender --command extension server-generate --repo-dir=/path/to/packages`, which builds an index.json listing from all the .zip extensions in --repo-dir (see the generated JSON API for details). Testing: add a new Remote Repository in Preferences (Get Extensions → Repositories → [+] → Add Remote Repository) and paste the generated JSON's location as the URL — for /path/to/packages that's file:///path/to/packages/index.json on Linux and macOS, file:///C:/path/to/packages/index.json on Windows, or file://HOST/share/path/to/packages/index.json for a Windows network share; a handy trick is to open file:/// in a browser, navigate to the repository, and copy that as the remote URL. Extensions listing HTML: server-generate can also build a simple website with the --html argument, `blender --command extension server-generate --repo-dir=/path/to/packages --html`, producing a ready-to-use index.html that lists extensions you can drop into Blender to install. Download links: to support drag-and-drop installation from a remote repository, the download URL must end in .zip, and you can append arguments to tell Blender what to do with the dropped URL — repository (a link, possibly relative, to the JSON used to install the repository), platforms (a comma-separated list of supported platforms; omitted means all OSes), blender_version_min (the minimum supported version, e.g. 4.2.0), and blender_version_max (the version that is not supported, earlier ones being supported). The more you supply, the better the experience, and every parameter except repository can come from the extension manifest. The arguments are URL-encoded into the expected format {URL}.zip?repository={repository}&blender_version_min={version_min}&blender_max={version_max_exclusive}&platforms={platform1,platform2}, for example `http://my-site.com/my-addon.zip?repository=.%2Findex.json&blender_version_min=4.2.0&platforms=windows-x64` (self-hosted) or `https://extensions.blender.org/download/sha256:57a6a5f39fa2cc834dc086a27b7b2e572c12fd14f8377fb8bd1c7022df3d7ccb/add-on-amaranth-v1.0.23.zip?repository=%2Fapi%2Fv1%2Fextensions%2F&blender_version_min=4.2.0&platforms=linux-x64%2Cmacos-x64` (the Extensions Platform), where %2F and %2C are simply the URL-encoded / and ,.

## How to Create Extensions

Creating an extension takes only a few steps: open the directory holding the add-on code or theme file, add a blender_manifest.toml with the required metadata (name, maintainer, ...), and use the Blender command-line tool to build the .zip. To publish to the Blender Extensions Platform, Install from Disk to confirm it works, then upload the .zip (requires a Blender ID); it's held for review and published once the moderation team approves. Extension files: an extension ships as a .zip holding a manifest plus other files, the exact set depending on type. An add-on extension needs at least the manifest and an __init__.py (more complex ones add .py files or wheels):
```text
my_extension-0.0.1.zip
├─ __init__.py
├─ blender_manifest.toml
└─ (...)
```
A theme extension needs only the manifest and the .xml theme file:
```text
my_extension-0.0.1.zip
├─ blender_manifest.toml
└─ theme.xml
```
Extensions may optionally keep all files inside a folder within the archive (common when saving a repository as ZIP from a version-control platform). Manifest: the file carrying all the metadata needed to process an extension. A good starting blender_manifest.toml for the .zip:
```text
schema_version = "1.0.0"

# Example of manifest file for a Blender extension
# Change the values according to your extension
id = "my_example_extension"
version = "1.0.0"
name = "My Example Extension"
tagline = "This is another extension"
maintainer = "Developer name"
# Supported types: "add-on", "theme"
type = "add-on"

# # Optional: link to documentation, support, source files, etc
# website = "

# # Optional: tag list defined by Blender and server, see:
# # 
# tags = ["Animation", "Sequencer"]

blender_version_min = "4.2.0"
# # Optional: Blender version that the extension does not support, earlier versions are supported.
# # This can be omitted and defined later on the extensions platform if an issue is found.
# blender_version_max = "5.1.0"

# License conforming to  (use "SPDX: prefix)
# 
license = [
"SPDX:GPL-3.0-or-later",
]
# # Optional: required by some licenses.
# copyright = [
# "2002-2024 Developer Name",
# "1998 Company Name",
# ]

# # Optional: list of supported platforms. If omitted, the extension will be available in all operating systems.
# platforms = ["windows-x64", "macos-arm64", "linux-x64"]
# # Other supported platforms: "windows-arm64", "macos-x64"

# # Optional: bundle 3rd party Python modules.
# # 
# wheels = [
# "./wheels/hexdump-3.3-py3-none-any.whl",
# "./wheels/jsmin-3.0.1-py3-none-any.whl",
# ]

# # Optional: add-ons can list which resources they will require:
# # * files (for access of any filesystem operations)
# # * network (for internet access)
# # * clipboard (to read and/or write the system clipboard)
# # * camera (to capture photos and videos)
# # * microphone (to capture audio)
# [permissions]
# network = "Need to sync motion-capture data to server"
# files = "Import/export FBX from/to disk"
# clipboard = "Copy and paste bone transforms"

# # Optional: advanced build settings.
# [build]
# paths_exclude_pattern = [
# "__pycache__/",
# "/.git/",
# "/*.zip",
# ]
```
Required values: blender_version_min (minimum supported version — use at least 4.2.0); id (a unique identifier); license (a list of SPDX license identifiers); maintainer; name (the full name); schema_version (the file-format version — use 1.0.0); tagline (a one-line description up to 64 characters, no trailing punctuation); type ("add-on" or "theme"); and version (following semantic versioning). Optional values: blender_version_max (the unsupported version, earlier ones supported); website; copyright (required by some licenses, formatted "Year Name" or "Year-Year Name"); tags (from the available list); platforms (omitted means all OSes; choices are "windows-x64", "windows-arm64", "macos-x64", "macos-arm64", "linux-x64"); wheels (relative paths to Python wheels); and permissions (the resources an add-on needs — files, network, clipboard, camera, microphone — each with a short single-sentence explanation up to 64 characters, no end punctuation). Optional "build" values, used only by the build subcommand: paths (manifest-relative file paths to include) and paths_exclude_pattern (gitignore-compatible patterns to exclude, which can't be set alongside paths); without a [build] table the default is
```text
[build]
paths_exclude_pattern = [
"__pycache__/",
".git",
"*.zip",
]
```
[build.generated] is reserved for internal use and must not appear in a TOML. Every value present in the manifest must be filled (no empty string "" or empty list []); simply omit any optional value you don't want.

Extensions can be built, validated, and installed from the command line. Build the package defined in the current directory with `blender --command extension build` (see the build docs). Validate the manifest without building via `blender --command extension validate`, and you can validate a package without extracting it first with `blender --command extension validate add-on-package.zip` (see the validate docs and the Extensions Command Line Arguments). To automate publishing updates on the Extension Platform, see the CI/CD documentation, and to host extensions yourself, see the Creating an Extensions Repository docs.
