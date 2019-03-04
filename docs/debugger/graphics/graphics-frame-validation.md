---
title: Graphics Frame-Überprüfung | Microsoft-Dokumentation
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a15a51d392ee6e351fbcf277ef26eb422fe7ecc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694815"
---
# <a name="graphics-frame-validation"></a>Grafik-Frame-Überprüfung
<!-- VERSIONLESS --> Visual Studio 2017 und höher unterstützt die **Frame-Überprüfung** Tool.  Die Frame-Überprüfung-Fenster werden Fehler und Warnungen im Zusammenhang mit der Ereignisliste angezeigt.  Um dieses Fenster anzuzeigen, wählen die **Ansicht > Frame-Überprüfung** Menü.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie auf die **Überprüfung ausführen** auf der linken oberen Ecke, um die Analyse zu initiieren.  Es dauert mehrere Minuten je nach Komplexität des Frames.  Die Daten, die angezeigt wird, hier ist eine Kombination aus beiden Quellen: die Nachrichten, D3D selbst ausgibt, wenn [SDK Layers](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) aktiviert ist, und die Daten, die vom Nachverfolgen von internen Zustand des Tools gesammelt werden. Nach Abschluss des Vorgangs sehen Sie mehrere Spalten mit Daten:


| **Spalte** | **Beschreibung** |
|------------| - |
| Ereignis-ID | ID, die zugeordnet ein Eintrag in wird der [Ereignisliste](graphics-event-list.md) Fenster. |
| Schweregrad | Beschädigung, Fehler, Warnung, Informationen oder Nachricht. |
| Kategorie | Anwendung definiert ist, verschiedene, Initialisierung, Bereinigung, Kompilierung, Status erstellen, Status festlegen, Status abrufen, Ausführung, Bearbeitung von Ressourcen und redundante und nicht verwendete-Shader. |
| Meldung | Die Meldung, die dem Ereignis zugeordnet wird. |
| event | Das Ereignis, das den Fehler oder die Warnung zugeordnet. |

## <a name="see-also"></a>Siehe auch
[Graphics Diagnostics (Debugging DirectX Graphics) (Grafikdiagnose (Debuggen von DirectX-Grafiken))](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->