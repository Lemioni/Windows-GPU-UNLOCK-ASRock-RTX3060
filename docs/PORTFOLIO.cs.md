# Text do portfolia

## Česky

### Experimentální Windows/UEFI port pro RTX 3060 na platformě AMD AM4

Realizoval jsem a hardwarově otestoval experimentální port projektu
Windows-GPU-UNLOCK pro ASRock B450M Pro4-F a RTX 3060 12 GB GA106.
Práce zahrnovala sběr preboot diagnostiky, odvození profilu konkrétního zařízení,
ověřování identity a otisků firmwarových ovladačů, simulované testování předání
GPU a měření výkonu před a po odemčení. Implementace a analýza vznikaly
s asistencí Codexu; fyzické spouštění a testování probíhalo na mém počítači.

V porovnatelném PyTorch benchmarku maticového násobení byl naměřen přibližně
74–79% nárůst propustnosti FP16/BF16/TF32 při stejném limitu 170 W.
FP32 výkon zůstal prakticky beze změny. Jde o výsledek konkrétní výpočetní
úlohy, nikoliv o tvrzení o stejném zrychlení her nebo všech AI aplikací.

Projekt rozšiřuje open-source práci impacifist/Windows-GPU-UNLOCK a
Zagitta/gpu-unlock. Původní odemykací algoritmus není mým autorstvím.
Příspěvkem je experimentální profil nové sestavy, diagnostické a testovací
úpravy a doložené měření na skutečném hardwaru.

Technologie: C, UEFI/EDK2, PCIe, PowerShell, Python, LLVM, PyTorch/CUDA,
hashování SHA-256, host replay a testování chybových stavů.

## English

### Experimental Windows/UEFI RTX 3060 port on AMD AM4

Implemented and hardware-tested an experimental Windows-GPU-UNLOCK extension
for an ASRock B450M Pro4-F system with a GA106 RTX 3060 12 GB. Work included
preboot diagnostics, exact-device profile extraction, firmware driver identity
checks, simulated GPU handoff tests and before/after performance measurement.
Implementation and analysis were AI-assisted with Codex; physical boot and
hardware validation were performed on my machine.

Matched PyTorch matrix-multiplication measurements showed approximately
74–79% higher FP16/BF16/TF32 throughput at the same 170 W power limit, with
essentially unchanged FP32 throughput. These results describe this workload,
not a general gaming or application speedup.

Built on impacifist/Windows-GPU-UNLOCK and Zagitta/gpu-unlock. My contribution
is the experimental machine-specific profile, diagnostic/test adaptations and
hardware evidence; I do not claim authorship of the original unlock algorithm.

## Krátký popis GitHub repozitáře

Experimental ASRock B450M Pro4-F / RTX 3060 GA106 Windows UEFI port, with
source-bound host tests and matched PyTorch benchmark evidence.

## Doporučená prezentace

- Forma: fork původního Windows projektu s vlastní větví a úvodem v README.
- Možný název větve: `codex/asrock-b450m-rtx3060`.
- Označení: experimentální, konkrétní sestava, jeden doložený úspěšný hardware pokus.
- Uváděj původní autory a asistenci AI; neslibuj podporu všech RTX 3060.
- Výkon dokládej tabulkou a anonymizovanými JSON soubory v `evidence/`.
