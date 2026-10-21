# Changelog

Complete release history. The README shows only Unreleased changes and the latest 3 formal versions.

### Unreleased

- Pulse Island now alerts you about Claude Code agents, so you no longer have to watch their windows. When a session needs your approval for a tool, an answer to a question, or a review of its plan, the island opens an alert panel with the project, the app it runs in, and how long it has waited. Open brings that terminal, editor, or the Claude app to the front, and Later puts the panel away. When a task finishes or stops with an error, the panel appears briefly and closes on its own, with other running or recently finished sessions listed below. While the island is expanded, alerts become a single strip above the module, and +N steps through the rest. While agent sessions are around, the collapsed island shows the Codex or Claude mark, a status light with the state (Running, Needs you, Done, Error), and how long instead of rotating system readings, taking turns when both have sessions and showing only the one that needs you when any does. When a session needs you, finished, or failed, hovering opens the alert panel first, and All Panels takes you to the usual panels; clicking the island still opens them directly. The alert panel also lists current system alerts such as memory or battery below a divider, and clicking one opens its module, so they are not missed while sessions hold the island. Alerts clear on their own when the app running the session quits or the session goes silent for 3 hours. Battery, memory, temperature, and disk alerts use the same look. Works with Claude Code in the desktop app, the terminal, and VS Code, and with Codex: click Connect alerts on the Codex page of AI Usage, then run `/hooks` in Codex to trust Pulse's hooks; the panel tells you while they still need trusting. Pulse receives only each session's state, its folder name, and the name of a built-in tool awaiting approval; it never reads prompts, replies, or commands, and keeps nothing. After updating, run `/reload-plugins` in open Claude Code sessions.

- Memos have a roomier layout that is easier to read: more line spacing and padding, and a memo of several lines shows its first line as a bold title over a two-line preview. Click a memo to expand its full text in place, select any part of it to copy, open its links, and copy, edit, pin, switch between memo and todo, or delete it from the expanded row; after deleting, the bottom bar briefly offers Undo. ⌘↩ in the input adds a todo. The editor grows with its text up to the visible height of the panel, Esc cancels an edit, and moving to another memo, changing the filter, or closing the panel saves it. Search highlights matches, and a memo whose match is far down previews from the match. Times show the time for today, “Yesterday”, or the date (with the year when it is not this year), and an expanded memo shows its full date and time. Pinning, completing, or switching type no longer changes a memo’s time or order. Clear completed is now a labeled button that appears only when there are completed todos.

- AI Usage now projects each limit window from its average pace since the window opened, showing “At this pace, runs out 19:42” or “about 54% by reset”, and stays quiet early in a window. Claude’s Token activity now shows the same figures as Codex: latest day, last 7/30 days, lifetime, the 14-day trend, peak day, streak, and longest turn. It comes from Claude Code sessions on this Mac since connecting and is labeled “This Mac”; claude.ai and other devices are not included. The Claude Code mod writes only each day’s token total and longest turn to `~/.claude/pulse-ai-usage-data` after each turn, without any conversation content, and disconnecting deletes them. After updating, run `/reload-plugins` in open Claude Code sessions.

- AI Usage tells Codex and Claude apart by their own colors: Claude’s signature orange and Codex’s blue-violet tint the logo, the selected tab, limit meters, and the 14-day trend, so the pinned panel reads at a glance. The “runs out” projection is now red so it never blends with Claude’s orange.

- AI Usage now shows the OpenAI logo for Codex and the Claude logo for Claude and gives both providers the same layout: Account limits shows the 5-hour and 7-day windows on two rows with used and remaining percentages and reset times, Codex model-specific limits are listed separately under Other limits, and Token activity sits in the same place for both. Anything a provider does not report is labeled as such instead of showing zero. Limits are named by window length rather than “Primary / Secondary”, which meant different windows for each provider. Also fixed the last row of the pinned AI Usage panel being clipped.

- Smoother scrolling in Applications, Clipboard and the Resource Monitor process lists, especially the first time they open: app icons now load in the background and appear once ready instead of stalling the scroll.

- Fixed the abrupt collapse after dismissing a Pulse Island notification: the notification row, the module panel below it and the island outline now shrink together in one animation, with the notification fading in place instead of jumping or sliding over the header, and no gap flashes between the island and the top of the screen when a notification appears or collapses.

- Added the Pixel Spectrum look: Resource Monitor, AI Usage and other readings use hand-drawn square pixel numerals; progress bars are rows of pixel cells whose color runs from cyan to red by position, so higher load lights warmer cells; CPU and memory shares use a pixel pie, system status uses glowing pixel lights, and the AI Usage 14-day trend uses pixel columns. Each module has its own color for the selected tab, a glow at the top of the panel, and the selected state of switches, filters and search fields. Clipboard entries show a colored badge for text, links, images and files, and Bluetooth batteries are pixel batteries colored by remaining charge.

- Adopted macOS 26 Liquid Glass: the expanded Pulse Island, module tab bar, toolbar buttons, filters, search fields, screenshot preview actions, and pinned panel backgrounds now use the native system glass, which lets the content behind show through and adapts automatically to accessibility settings such as Reduce Transparency. The minimum system requirement is now macOS 26.0.

- Unified the look of every Pulse Island module and pinned panel: modules now switch from an always-visible tab bar, Resource Monitor uses metric cards, and groups, buttons, filters, search fields, notices, and empty states share one style with the action bar in the same place everywhere. Clipboard and Memos keep their search field in the bottom bar, Memos shows counts in its filter and uses a single-line input that grows with its text, and Bluetooth groups devices into Connected and Disconnected with compact battery levels. Screenshots keeps its vertical list, now in the same grouped style.

- Added a display control to pinned AI Usage and Resource Monitor panels. Each panel independently remembers whether to follow across displays or stay on its current display; Resource Monitor supports this in both full and minimal layouts. Pinned panels group their display, pin and resize controls in one place and show them only on hover instead of in a permanent bottom bar.

- Fixed AI Usage showing outdated Claude quotas after a subscription plan change: with several Claude Code sessions open, Pulse now keeps the reading Claude received most recently, so reopened older sessions and readings past their reset no longer override current quotas. After updating, restart open Claude Code sessions (or run `/reload-plugins`) to load the updated mod.

- Fixed the pinned AI Usage panel staying on the previous display; it now follows the pointer between displays like Resource Monitor while preserving its relative position.

- Fixed an extra background frame appearing while Pulse Island expands, collapses, or reverses direction quickly; the glass effect now follows the island outline throughout the animation.

- Claude usage no longer turns “Out of date” shortly after Claude Code goes idle. Data is marked out of date only after one hour or once a reset time passes; the mini panel omits “Updated just now” and “Updated N min ago” labels.

- The expanded Pulse Island is now one continuous surface: the header stays solid black so the menu bar never shows through, and the module panel and notification suggestions below use a dark glass material that blurs what is behind the island. With Reduce Transparency on, the island keeps its solid black look. Transparent areas beside the expanded panel no longer intercept clicks.

- Fixed Claude Desktop connections that created a mod without loading it. Connecting now registers the loading configuration and preserves other plugin settings on disconnect.

- AI Usage now switches between Codex and Claude, with a separate floating panel showing both providers’ 5-hour and 7-day usage as segmented bars in a compact layout that matches the resource mini panel’s material surface without a title or window shadow, with display and pin controls appearing only while the panel is hovered, including when locked to a display and the next reset time below each 5-hour and 7-day usage bar, showing only HH:mm for today and a date with time for other days. Claude connects through an official Claude Code mod for Desktop, terminal, and VS Code, preserves and restores the existing status line, and clearly marks missing or out-of-date data.

- Fixed the island panel opening when the pointer moves over browser tabs or other controls below it; hover and click targets now follow the visible island boundary.
- Added a generic AI Usage module whose first Codex provider keeps quota buckets separate, shows used and remaining percentages plus reset times, and adds account-level latest-day, 7/30-day, lifetime-token, 14-day trend, peak, streak, and longest-turn metrics. It reads on demand through the documented App Server of an installed, signed-in Codex CLI, retains the last successful snapshot after refresh failures, and surfaces explicit errors.
- Fixed Pulse Island using a non-full battery icon at a displayed 100%; low-battery and charging icons now use system symbols, and generic Bluetooth battery icons follow the reported charge level.
- Improved Uninstall and Clean Up permission guidance: the confirmation window now explains why App Management or Full Disk Access may be needed, offers direct System Settings buttons, and shows a simpler warning card plus failed paths when permission is the only blocker.
- Clipboard records now show both the full date and time in the top-right corner, making entries from different days easy to distinguish.

### 2.5.0 - 2026-06-17

- The Bluetooth panel now shows a top notice when system Bluetooth is off and offers a Turn On handoff to Bluetooth Settings, so the state is not mistaken for an empty device list.
- Added a suggestion panel between the island header and main panel for dismissible storage, power, thermal, memory pressure, and Bluetooth battery suggestions; when multiple suggestions are active, one item expands as a full card in the same horizontal queue while the others collapse into circular icons, and clicking an icon linearly expands it in place while switching to the owning panel. The panel can still be turned off in Settings.
- The Applications module now opens right-click Uninstall and Clean Up in a regular confirmation window that scans the app bundle and common local Library leftovers, then moves only user-selected items to the system Trash.
- Uninstall and Clean Up now explains why macOS may ask for App Management or app-data permission. The confirmation flow no longer runs inside the island panel, and the island collapses after the uninstall window opens so macOS authorization prompts are not covered by the island layer; on permission failure, Pulse opens App Management or Full Disk Access settings and lets users retry only the failed items after granting permission.
- Full-screen screenshots and recordings now choose a target display first, so multi-display setups no longer fall into window selection; window recording continues to use the native macOS window picker.
- The screenshot editor now opens centered on the current screen and collapses the island preview before editing, so small images are not covered by the top panel.
- Release archive: [Pulse-2.5.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.5.0/Pulse-2.5.0.dmg); SHA-256: `38da615c20d487aa5d1bb8929420b53015af662fa860ac4874376d611dcaa612`.

### 2.4.0 - 2026-06-03

- Renamed the Screenshots module to Capture and added native recording actions below the existing full-screen, window, and selection screenshot actions; full-screen and window target selection still reuse the native macOS screenshot picker, custom-region recording uses local selection and recording guide layers that dim unselected areas, and recording output is written with ScreenCaptureKit + AVFoundation.
- After recording starts, the Pulse island shows elapsed time and a stop button; when Hide Pulse is enabled, Pulse is hidden before target selection and excluded from the final recording output.
- Each recording mode can also have a global shortcut set from the Capture panel or Settings; shortcuts follow the Hide Pulse and Hide Mouse options, and triggering the same mode while it is recording stops the recording and opens an island video preview so the user can play, save, share, close, or discard the temporary `.mov`.
- Screenshot and video previews now use a top-right close button. It exits the preview directly, restores the expanded island when the preview started from an expanded panel, and removes an unsaved temporary `.mov` when closing a video preview.
- Added Hide Pulse and Hide Mouse options so screenshots can hide Pulse before capture, recordings can exclude Pulse from saved videos, and recordings can hide the pointer for cleaner screen videos.
- Refined Capture panel icons and mode labels: recording actions now use dedicated icons, recording buttons reuse the Full Screen, Window, and Selection mode names, and Hide Pulse uses a clearer dedicated icon.
- Added a Memo module for local notes and todos in the Pulse island, with a larger full-width composer that creates notes on Return, right-click Set as todo, all/notes/todo/done filters, search, editing, pinning, copy, delete, and clearing completed todos. All memo content stays local.
- Release archive: [Pulse-2.4.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.4.0/Pulse-2.4.0.dmg); SHA-256: `5937825a99e43f2fbf599cd2efb9d871ba16e339bac1b73a504db553c2e3bdae`.

### 2.3.0 - 2026-06-01

- Added a Screenshots module with native macOS full-screen, window, and selection capture modes; full-screen capture opens the native display picker for confirmation first, window capture omits the system window shadow, captures are written to the system clipboard, the island shows an image preview reminder after capture and auto-collapses after 3 seconds only when it is not hovered, the reminder exposes explicit Save, Share, Edit, foreground pinning, local text-recognition, and direct preview-drag export actions, and each mode can have its global shortcut set directly in the Screenshots panel without requiring modifier keys.
- Added a bottom Screenshots panel option to hide Pulse while capturing. It is on by default; turning it off lets users include Pulse itself in screenshots, and both panel actions and screenshot shortcuts follow the setting.
- The screenshot completion reminder now includes an Edit action that opens a pinned-image-style foreground floating editor, with a light-mode white and dark-mode adaptive icon toolbar below the image. The toolbar starts with a separated hand Move button and then offers rectangles, circles, arrows, pen strokes, mosaic redaction, text, undo, save, share, pin, cancel, and done.
- Mosaic redaction in the screenshot editor now uses source-image pixelation with a brush stroke, letting users cover along content contours instead of drawing only rectangular regions.
- Refined the screenshot editor text tool: text input now uses a transparent, center-aligned field, clicking the canvas commits the input, and existing text labels can be dragged to reposition them.
- Pinned screenshot floating windows keep the same borderless image-window style and now use native macOS window resizing while preserving the original image aspect ratio.
- Fixed the screenshot editor starting with Mosaic selected and accidentally adding redaction while dragging the image; it now starts with no selected tool, and selecting a tool locks the image area so drawing does not move the editor window.
- Fixed canceling the native macOS screenshot picker showing the previous screenshot preview; Pulse now shows the completion reminder only when the current capture writes a new clipboard image.
- The Screenshots panel now shows an orange authorization notice when macOS Screen Recording permission has not been granted, clarifying that captures only run after a user click or shortcut.
- Added a Bluetooth module that lists local Bluetooth devices, connection state, and readable battery levels; single-battery devices such as keyboards, trackpads, and mice show one circular battery indicator, Apple HID devices lightly alternate the center battery icon with a bolt when macOS returns charging state, AirPods-style devices show left, right, and case battery levels when macOS returns them, and paired devices can be connected or disconnected from the list.
- Bluetooth devices at or below 20% or 10% now reuse the Pulse Island two-line alert style, colors, and animation for local low-battery reminders; each continuous low-battery state is shown once.
- Refined the screenshot completion reminder header so its icon, title, and completion state align with the island's top row.
- Added a Copy item action to the Clipboard record context menu, letting users write a saved record back to the system clipboard from right-click.
- Fixed a case where launching some apps from the Applications module could collapse the island panel and immediately reopen it from a stale hover event.
- Release archive: [Pulse-2.3.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.3.0/Pulse-2.3.0.dmg); SHA-256: `66be3ba207946b71e449bf547a963bd4c4bd8f15d780146235958bb405c3efde`.

### 2.2.0 - 2026-05-27

- Expanded system compatibility: the minimum system requirement is now macOS 15.0 instead of macOS 26.0; macOS 26 and later continue to use the existing clipboard permission status and favorite-removal drag feedback paths.
- Release archive: [Pulse-2.2.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.2.0/Pulse-2.2.0.dmg); SHA-256: `47aa82f18b1b44af26ed31fa66224bd7f5564a914cc42d7513e0e83b871c86fb`.

### 2.1.0 - 2026-05-27

- Refined the transition from resting state to expanded state: the header text, icon, and common action buttons now fade in after the island begins opening, making the expansion feel less abrupt.
- Moved common actions into the expanded-state header: Settings and Quit now sit at the top right, while the Resource Monitor footer only keeps panel-specific controls; pinned panels now place Minimize at the bottom right.
- Simplified the Resource Monitor panel by removing the repeated Pulse title, device name, and pixel icon; the expanded-state Resource Monitor footer now shows the refresh time, while pinned panels no longer show time.
- Improved multi-display behavior: the Dynamic Island-style entry and pinned Resource Monitor panel now follow the current display, so switching between external monitors feels more consistent.
- Changed expanded-state module switching to a horizontal selector: Resource Monitor and Applications now sit in one row, click or row-wide left/right swipes switch modules, the selected module stays centered, and swipe direction follows natural paging.
- After first launch or restart, expanding the island now defaults to the Applications module so users can launch favorite apps directly.
- Added the Clipboard module: Pulse records text, links, files, images, and sensitive or transient markers by default, keeps history locally, supports filtering by all/text/images/links/files plus search, copy, reveal, delete, and clear actions, supports double-click direct paste into the currently focused target when Accessibility permission allows it, and lets users adjust entry and time retention in Settings; duplicate payloads are merged into one history entry, copying from Clipboard history does not add another entry, sensitive entries are masked by default while copying the complete original payload, and OCR is off by default and local-only.
- Fixed mojibake when some apps provide clipboard text as UTF-16 without a byte-order mark; matching local history entries repair their display text on next launch.
- Added a Shortcuts area in Settings for separate global shortcuts that wake Clipboard or Applications; shortcuts are stored only in local preferences.
- Shortcut wake now reuses the mounted island panel and opens directly into the target module, making the expansion feel closer to pointer hover.
- The resting island now shows a 1.5-second minimal confirmation when Clipboard saves a new record, using a content-type icon, Copied label on non-notched screens, and completion checkmark without opening the panel or changing the data boundary.
- Clearing clipboard history now asks for confirmation inline in the footer, preventing accidental removal of all records.
- Added a single-row Favorite Apps panel in the Applications module: the module now opens in icon view by default, icon view supports dragging apps into favorites, list view uses a pin button to add or remove favorites quickly, favorites can be reordered by dragging or removed by dragging them back to the app area, and running apps show a highlighted dot below their icons.
- Opening an app from the Applications module now returns Pulse to its resting state, reducing overlap while the target app launches.
- Smoothed Favorite Apps drop placement: dragging or reordering an app between two favorites now reserves the real landing width, reducing the jump after release.
- Release archive: [Pulse-2.1.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.1.0/Pulse-2.1.0.dmg); SHA-256: `fd784f829c28e672fd88f94024ecd9a4fe08ca60492154d632040a9274249017`.

### 2.0.0 - 2026-05-25

- Pulse now works like a Dynamic Island-style surface at the top of the screen, becoming the only primary entry point without a menu bar icon or menu bar status panel; Settings, updates, the pinned panel, and Quit remain available from the expanded state.
- Added the resting state: Pulse stays at the top center and lightly rotates between memory and CPU; when a Mac is on battery or charging from a low level at or below 20%, battery level joins the rotation with 20%, 10%, or charging icons.
- Hovering over Pulse opens the expanded state, with a Resource Monitor header and the full status panel below.
- Added the alert state: when a Mac is on battery at or below 10%, thermal state becomes critical, storage is extremely low, or memory pressure is high, Pulse briefly shows a more visible two-line alert, then returns to the resting state after 3 seconds; each continuous condition is shown once.
- Refined resting-state rotation with vertical rolling and numeric text transitions while respecting the system Reduce Motion setting.
- The expanded-state header supports horizontal module switching; the new Applications module opens local apps from standard application locations in either list view or a Launchpad-like icon view.
- Fixed Pulse placement on MacBooks with a camera housing by avoiding the hidden top-center area.
- Release archive: [Pulse-2.0.0.dmg](https://github.com/dorrrway/pulse/releases/download/v2.0.0/Pulse-2.0.0.dmg); SHA-256: `eb19283e73273f8df1f70e466888aa95f95ef25dec227eaa129a4ca21ac46028`.

### 1.2.0 - 2026-05-15

- Fixed Language > System sometimes showing English under macOS settings whose preferred language is Chinese; Pulse now matches supported languages from the system preferred-language list.
- Fixed Appearance > System not immediately refreshing open windows after switching back from Light or Dark mode.
- Improved the DMG installer window with bilingual drag guidance and fixed Pulse-to-Applications layout.
- Release archive: [Pulse-1.2.0.dmg](https://github.com/dorrrway/pulse/releases/download/v1.2.0/Pulse-1.2.0.dmg); SHA-256: `4549673b0017257a46326c5f6b91f8833ddd98a386c218bda484c8bac6e45c95`.

### 1.1.4 - 2026-05-14

- Fixed the pinned floating panel Update button staying gray under system rendering while preserving its original size.
- The settings page now shows the current app version at the bottom.
- Release archive: [Pulse-1.1.4.dmg](https://github.com/dorrrway/pulse/releases/download/v1.1.4/Pulse-1.1.4.dmg); SHA-256: `36147b065eea136d272502bbb09c5d054cafe54c174acd33deb73080a1717d6e`.

### 1.1.3 - 2026-05-14

- Refined the full-panel update prompt: in pinned floating panels, the Update button now sits after the minimize control and uses a more visible blue background.
- Release archive: [Pulse-1.1.3.dmg](https://github.com/dorrrway/pulse/releases/download/v1.1.3/Pulse-1.1.3.dmg); SHA-256: `fd8d4116081d4eaad0c03113fd08489b64b855f0d8cb688653cf293e078f82b9`.

### 1.1.2 - 2026-05-14

- Moved update checks to the TimeLikeSilver-hosted appcast endpoint so update checks can aggregate runtime trends; requests still do not attach system metrics, files, process lists, app bundle paths, persistent tracking identifiers, or Sparkle system profiling data.
- Refined full-panel status dots and CPU ranking warning colors so high-CPU app names and values use the same staged color feedback.
- Release archive: [Pulse-1.1.2.dmg](https://github.com/dorrrway/pulse/releases/download/v1.1.2/Pulse-1.1.2.dmg); SHA-256: `aac8429ff0a48e4f44767e95ca9d42a205e13f9138e31016d9d35dfb9a6b0726`.

### 1.1.1 - 2026-05-14

- Adjusted the high-activity threshold for disk I/O and reduced Pulse's own refresh overhead without slowing real-time CPU, memory, network, or disk I/O updates.

### 1.1.0 - 2026-05-14

- Added a pinnable floating panel and minimal mode for switching between the full status panel and a compact metrics view.
- Added CPU and memory usage rankings with local app/process usage, app icons, pixel share charts, and detail popovers.
- Refined full-panel status feedback with System Runtime, status-colored memory, thermal, power, and disk I/O cards, and warning colors for high CPU usage.
- Added Sparkle updates, allowing new versions to be downloaded, verified, and installed from the panel.
- Added Appearance and Contact settings, and simplified the startup and language settings.
- Improved menu bar and floating panel layout, made metric feedback more responsive, and fixed theme syncing, settings-window focus, and floating-panel stability issues.
- Updated the privacy wording to clarify local use of process names, app bundle paths, resource usage, and update checks without uploading system metrics or profiling data.

### 1.0.0

- Initial release with a menu bar system status panel, CPU, memory, disk, network, battery, thermal state, and disk I/O metrics, Light and Dark Mode support, and launch-at-login settings.
