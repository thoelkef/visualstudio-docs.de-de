---
title: Grafikframe-Überprüfung | Microsoft-Dokumentation
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
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735502"
---
# <a name="graphics-frame-validation"></a>Grafikframe-Überprüfung
<!-- VERSIONLESS -->
Ab Visual Studio 2017 wird das Tool **Frame-Überprüfung** unterstützt.  Im Fenster „Frame-Überprüfung“ werden Fehler und Warnungen im Zusammenhang mit der Ereignisliste angezeigt.  Um dieses Fenster anzuzeigen, wählen Sie das Menü **Ansicht > Frame-Überprüfung** aus.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie in der linken oberen Ecke auf die Schaltfläche **Überprüfung ausführen**, um die Analyse zu initiieren.  Je nach Komplexität des Frames kann dieser Vorgang mehrere Minuten dauern.  Die hier angezeigten Daten sind eine Kombination aus zwei Quellen: den Nachrichten, die D3D ausgibt, wenn [SDK-Layer](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) aktiviert sind, und den Daten, die von der eigenen internen Zustandsüberwachung des Tools gesammelt werden. Nach Abschluss des Vorgangs werden mehrere Datenspalten angezeigt:

| **Spalte** | **Beschreibung** |
|------------| - |
| Ereignis-ID | ID, die einem Eintrag im Fenster [Ereignisliste](graphics-event-list.md) zugeordnet ist. |
| Schweregrad | Beschädigung, Fehler, Warnung, Info oder Meldung. |
| Kategorie | Anwendung definiert, Verschiedenes, Initialisierung, Bereinigung, Kompilierung, Zustandserstellung, Zustandseinstellung, Zustandsabruf, Ausführung, Ressourcenbearbeitung, Shader, Redundant und Nicht verwendet. |
| Meldung | Die dem Ereignis zugeordnete Meldung. |
| event | Das dem Fehler oder der Warnung zugeordnete Ereignis. |

## <a name="see-also"></a>Siehe auch
[Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->