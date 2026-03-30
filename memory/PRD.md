# PRD — DL Store (GitLab-synced APK Repository Site)

## Original Problem Statement
Build a clone of aPatche/index.html with these modifications:
- Rebrand to "DL Store"
- Provider button "rupanh123-phap" redirects to phap.vercel.app
- Image icons on APK provider menu (customizable via Find & Replace)
- Sync app list from GitLab (quangvinh0097/ng-d-ng-anriod-tv-mod)
- Ignore .gitkeep and README files
- Categories ordered as GitLab folders: APK Fix, Laucher Mod, etc.
- App buttons link to raw GitLab download URLs

## Architecture
Single-file static HTML (dl-store.html):
- TailwindCSS CDN + Lucide icons + Inter font
- GitLab REST API v4 (no auth, public repo) for auto-sync
- Vanilla JS for all logic

## What's Implemented

### 2026-03-30
- [x] DL Store branding (header, title, favicon)
- [x] Provider modal with image icons — `ICON_DLSTORE_PLACEHOLDER` / `ICON_PHAP_PLACEHOLDER`
- [x] rupanh123-phap button → https://phap.vercel.app
- [x] Auto-sync from GitLab API on page load
- [x] Loading skeleton cards while fetching
- [x] Categories = GitLab top-level folder names (maintained in GitLab order)
- [x] Ignore .gitkeep, README.md, .gitignore, .DS_Store
- [x] Only APK-type files shown (.apk, .xapk, .apkm, .apks, .apkx)
- [x] App cards → raw GitLab download links
- [x] APP_ICON_MAP for per-app custom icons + DEFAULT_APP_ICON placeholder
- [x] Manual "Đồng bộ lại" refresh button
- [x] Warning modal (10s countdown) + Provider selection modal
- [x] Dark/light mode toggle
- [x] Sync status bar (timestamp + app count)
- [x] Error state with retry button

## Find & Replace Guide for Customization
| Placeholder | Replace With |
|---|---|
| `ICON_DLSTORE_PLACEHOLDER` | URL ảnh icon DL Store |
| `ICON_PHAP_PLACEHOLDER` | URL ảnh icon PhuocPhap |
| `ICON_APP_DEFAULT_PLACEHOLDER` | URL ảnh icon mặc định cho tất cả app |

## GitLab Folders (Categories)
APK Fix, APK Mod, APK Tool, AppDrawer, Ban Phim Anriod TV,
IPTV, KHO UNG DUNG _ TRINH DUYET, Laucher Mod,
PHIM_TRUYEN HINH_THE THAO, Quan Li File, TRUYEN HINH, YOUTUBE

## Output File
`/app/index.html` — standalone HTML, copy and host anywhere (dl-store.html đã xóa)

## Backlog / Future
- P1: Add icon URL config file in GitLab so icons auto-update from repo
- P2: Recurse into subfolders (currently skips YOUTUBE/SUPER-VOICE etc.)
- P2: App display name override map (currently auto-formatted from filename)
- P3: Search/filter by app name
