# Survey: Baldo The guardian owls (0100A75005E92000)

- display version: 1.1.0
- base: `Baldo_The_guardian_owls_[0100A75005E92000].xci` (1.56 GB)

## Code modules

| module | what | build ID | text / ro / data (MB) | bss (MB) |
|---|---|---|---|---|
| main | the game | `ab144284dedf3943904e838143634a73` | 36.4 / 18.2 / 3.6 | 3.5 |
| rtld | rtld | `c1ed34fd7d1962277a4555d9ec714657` | 0.0 / 0.0 / 0.0 | 0.0 |
| sdk | nnSdk | `d9add76fc264863d85fbbd1d70076c76` | 5.5 / 6.5 / 0.4 | 0.6 |
| subsdk0 | NintendoSDK_movie | `84e50460493a12f26100e5150fbff271` | 3.3 / 2.1 / 0.2 | 1.1 |

- main.npdm program ID: `0100A75005E92000`
- system resource: 16 MB
- SDK: 10_4_1 (Mario: 16_2_0 / 16_2_12)
- SDK components: NintendoSDK_NVN-10_4_1, NintendoSDK_libcurl-10_4_1, NintendoSDK_libz-10_4_1, NintendoSDK_movie-10_4_1, NintendoSdk_nnSdk-10_4_1
- Unity: 2019.4.8f1
- engine and API markers: NVN (main, sdk, subsdk0); Unity IL2CPP (main); Unity (main); FMOD (main)

## RomFS: 20 files, 0.86 GB

| top level | files | GB |
|---|---|---|
| Data/StreamingAssets | 10 | 0.50 |
| Data | 7 | 0.35 |
| Data/Managed | 2 | 0.01 |
| Data/Resources | 1 | 0.00 |

| header magic | files | GB |
|---|---|---|
| UnityFS | 8 | 0.78 |
| FMOD | 4 | 0.07 |
| PNG | 1 | 0.00 |

extensions: `.bundle` 7, `.resource` 4, `.dat` 2, `(none)` 2, `.xml` 1, `.json` 1, `.png` 1, `.config` 1, `.unity3d` 1

## Rewrite-site census (insn_census.py)

```
/home/hatch/workspace/nx2a-baldo/0100A75005E92000_survey/extract/ExeFS/main: 9543999 instructions decoded (119 undecodable words)
  x18 use                19429
/home/hatch/workspace/nx2a-baldo/0100A75005E92000_survey/extract/ExeFS/sdk: 1443983 instructions decoded (273 undecodable words)
  x18 use                11659
  svc                    61
  mrs tpidrro_el0        60
  mrs cntpct_el0         33
  msr tpidr_el0          3
  mrs tpidr_el0          2
  svc numbers: #1 x1, #2 x1, #3 x1, #4 x1, #5 x1, #6 x1, #7 x1, #8 x1, #9 x1, #0xa x1, #0xb x1, #0xc x1, #0xd x1, #0xe x1, #0xf x1, #0x10 x1, #0x11 x1, #0x12 x1, #0x13 x1, #0x14 x1, #0x15 x1, #0x16 x1, #0x17 x1, #0x18 x1, #0x19 x1, #0x1a x1, #0x1b x1, #0x1c x1, #0x1d x1, #0x1f x1, #0x21 x1, #0x22 x1, #0x23 x1, #0x25 x1, #0x26 x1, #0x27 x1, #0x28 x1, #0x29 x1, #0x2a x1, #0x2c x1, #0x2d x1, #0x2f x1, #0x32 x1, #0x33 x1, #0x34 x1, #0x35 x1, #0x36 x1, #0x40 x1, #0x41 x1, #0x43 x1, #0x44 x1, #0x45 x1, #0x48 x1, #0x49 x1, #0x4b x1, #0x50 x1, #0x51 x1, #0x52 x1, #0x53 x1, #0x70 x1, #0x72 x1
/home/hatch/workspace/nx2a-baldo/0100A75005E92000_survey/extract/ExeFS/subsdk0: 872702 instructions decoded (314 undecodable words)
  x18 use                10203
```

## Imports vs host hooks (nso_syms.py)

```
HLE hooks in host: 962 | present in new game sdk exports: 774
main imports: old game 0, new game 914, shared 0, new-only 914

new game main imports by area (total / not imported by old game):
  C / libc                 206 /  206
  nn::hid                  103 /  103
  other C++                 95 /   95
  nn::os                    89 /   89
  nn::friends               71 /   71
  nn::ec                    63 /   63
  nn::audio                 47 /   47
  nn::socket                44 /   44
  nn::fs                    39 /   39
  nn::account               26 /   26
  nn::swkbd                 24 /   24
  nn::irsensor              24 /   24
  nn::oe                    19 /   19
  nn::nifm                  10 /   10
  nn::ngc                    7 /    7
  nn::mem                    7 /    7
  nn::err                    6 /    6
  nn::ssl                    6 /    6
  nn::time                   5 /    5
  nn::vi                     4 /    4
  nn::aoc                    4 /    4
  nn::diag                   3 /    3
  nn::util                   3 /    3
  nn::pl                     3 /    3
  nn::cstd                   2 /    2
  nvn                        1 /    1
  nn::crypto                 1 /    1
  nn::settings               1 /    1
  nn::nsd                    1 /    1

examples of new-only imports per area:
  C / libc: _Unwind_Resume, __assert_fail, __cxa_allocate_exception, __cxa_begin_catch
  nn::hid: _ZN2nn3hid12GetNpadStateEPNS0_16NpadFullKeyStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_16NpadJoyDualStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_16NpadJoyLeftStateERKj, _ZN2nn3hid12GetNpadStateEPNS0_17NpadHandheldStateERKj
  other C++: _ZN2nv18InitializeGraphicsEPvm, _ZN2nv20SetGraphicsAllocatorEPFPvmmS0_EPFvS0_S0_EPFS0_S0_mS0_ES0_, _ZN2nv28SetGraphicsDevtoolsAllocatorEPFPvmmS0_EPFvS0_S0_EPFS0_S0_mS0_ES0_, _ZN5movie11SetCoreMaskEm
  nn::os: _ZN2nn2os10ClearEventEPNS0_9EventTypeE, _ZN2nn2os10WaitThreadEPNS0_10ThreadTypeE, _ZN2nn2os11FreeTlsSlotENS0_7TlsSlotE, _ZN2nn2os11GetHostArgcEv
  nn::friends: _ZN2nn7friends10InitializeEv, _ZN2nn7friends12AsyncContext6CancelEv, _ZN2nn7friends12AsyncContext7HasDoneEPb, _ZN2nn7friends12AsyncContextC1Ev
  nn::ec: _ZN2nn2ec19ShopServiceAccessor10InitializeERKNS0_11ShopServiceE, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse3GetEPvm, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse4WaitEv, _ZN2nn2ec19ShopServiceAccessor13AsyncResponse6CancelEv
  nn::audio: _ZN2nn5audio12StopAudioOutEPNS0_8AudioOutE, _ZN2nn5audio13AddDeviceSinkEPNS0_19AudioRendererConfigEPNS0_14DeviceSinkTypeEPNS0_12FinalMixTypeEPKaiPKc, _ZN2nn5audio13CloseAudioOutEPNS0_8AudioOutE, _ZN2nn5audio13ListAudioOutsEPNS0_12AudioOutInfoEi
  nn::socket: _ZN2nn6socket10GetSockOptEiiiPvPj, _ZN2nn6socket10InitializeEPvmmi, _ZN2nn6socket10InitializeERKNS0_6ConfigE, _ZN2nn6socket10SetSockOptEiNS0_5LevelENS0_6OptionEPKvj
  nn::fs: _ZN2nn2fs10CreateFileEPKcl, _ZN2nn2fs10DeleteFileEPKc, _ZN2nn2fs10RenameFileEPKcS2_, _ZN2nn2fs11GetFileSizeEPlNS0_10FileHandleE
  nn::account: _ZN2nn7account10InitializeEv, _ZN2nn7account11GetNicknameEPNS0_8NicknameERKNS0_3UidE, _ZN2nn7account12AsyncContext6CancelEv, _ZN2nn7account12AsyncContext7HasDoneEPb
  nn::swkbd: _ZN2nn5swkbd10MakePresetEPNS0_14KeyboardConfigENS0_6PresetE, _ZN2nn5swkbd10SetSubTextEPNS0_14KeyboardConfigEPKDs, _ZN2nn5swkbd12SetGuideTextEPNS0_14KeyboardConfigEPKDs, _ZN2nn5swkbd12ShowKeyboardEPNS0_6StringERKNS0_15ShowKeyboardArgE
  nn::irsensor: _ZN2nn8irsensor10InitializeERKNS0_14IrCameraHandleE, _ZN2nn8irsensor15RunHandAnalysisERKNS0_14IrCameraHandleERKNS0_18HandAnalysisConfigE, _ZN2nn8irsensor17GetIrCameraHandleERKj, _ZN2nn8irsensor17GetIrCameraStatusERKNS0_14IrCameraHandleE
  nn::oe: _ZN2nn2oe15SetCpuBoostModeENS0_12CpuBoostModeE, _ZN2nn2oe16GetOperationModeEv, _ZN2nn2oe17EnableCrashReportEv, _ZN2nn2oe17GetPseudoDeviceIdEPNS_4util4UuidE
  nn::nifm: _ZN2nn4nifm10InitializeEv, _ZN2nn4nifm18IsNetworkAvailableEv, _ZN2nn4nifm19SetLocalNetworkModeEb, _ZN2nn4nifm20CancelNetworkRequestEv
```

## What it means for a port

- modules besides main / sdk: subsdk0 (NintendoSDK_movie); the provisional profile loads main subsdk0 sdk (load order main, subsdk*, sdk)
- Unity: the shaders are Shader objects in UnityFS bundles and data.unity3d, which shader_split.py reads through unityfs.py (written for Unity 2020.3's Switch format, also read for 2017.4, 2018.3, 2022.3 and 6000.0; check other Unity versions first)
- main has 10 GLSLC compiler output magics (0x19866891): shader_split.py takes those that are whole outputs (13 Sentinels and the KTGL games compile their shaders into main; Unity's player has 11 of its own)
- SDK 10, not Mario's 16: NVN object sizes, API version and service layouts differ by SDK (the host was converted from D2R's SDK 12 to SDK 16 sizes); check them one by one per docs/agents/03

## Provisional profile keys (dm/games/profile_guess.py)

What the game files decide; mem_used follows the rewrite, and a game with virtual address memory that sets a heap gets a heap check on the Mac (scripts/build_ipa_from_nsp.py heap_check).

```
modules	main subsdk0 sdk	# every module main imports from
mem_reserve	0x140000000	# the NPDM declares 16 MB of system resource (virtual address memory) and main sets a heap: a 5 GB block with a large alias region; the heap check sizes the heap region from the heap the game asks for
mem_alias	0x118000000
mem_stack	0x10000000
app_pool	0xCD500000
sys_resource	0x1000000	# the NPDM declares 16 MB of system resource
```

Next steps: docs/agents (02 survey, 03 bring-up).
