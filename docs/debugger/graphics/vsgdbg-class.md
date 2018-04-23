---
title: VsgDbg-Klasse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c48142d3458cf3c85b0391fcf33dc7238d16abb2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="vsgdbg-class"></a>VsgDbg-Klasse
Stellt eine Schnittstelle für die programmgesteuerte Kontrolle der In-App-Komponente der Grafikdiagnose dar.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Member  
 Die `VsgDbg`-Klasse unterstützt die folgenden Member:  
  
### <a name="public-constructors"></a>Öffentliche Konstruktoren  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Erstellt eine Instanz der `VsgDbg`-Klasse und bereitet optional die In-App-Komponente der Grafikdiagnose vor, Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|  
|[VsgDbg::~VsgDbg (Destructor)](vsgdbg-tilde-vsgdbg-destructor.md)|Zerstört eine Instanz der `VsgDbg`-Klasse.|  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Fügt dem Grafikdiagnose-HUD (Head-up-Display) eine benutzerdefinierte Meldung hinzu.|  
|[BeginCapture](begincapture.md)|Startet ein Erfassungsintervall, das mit `EndCapture` endet.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.|  
|[Kopieren (Programmgesteuerte Aufzeichnung)](copy-programmatic-capture.md)|Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.|  
|[EndCapture](endcapture.md)|Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.|  
|[Init](init.md)|Bereitet die In-App-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|  
|[ToggleHUD](togglehud.md)|Schaltet die Grafikdiagnose-HUD-Überlagerung ein oder aus.|  
|[UnInit](uninit.md)|Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.|  
  
## <a name="remarks"></a>Hinweise  
 Die `VsgDbg`-Klasse stellt eine Schnittstelle dar, die Sie verwenden können, um Grafikdiagnosefunktionen programmgesteuert zu steuern. Sie können einige Funktionen sogar dann verwenden, wenn Sie Grafikinformationen nicht aktiv erfassen und aufzeichnen. Hierzu gehören die `AddMessage`-Memberfunktion und die `ToggleHUD`-Memberfunktion. Die anderen Memberfunktionen bereiten entweder die In-App-Komponente der Grafikdiagnose vor, um die aktive Erfassung von Grafikinformationen zu starten oder zu beenden, oder sie müssen aufgerufen werden, während die App aktiv Grafikinformationen in einer Grafikprotokolldatei erfasst und aufzeichnet.