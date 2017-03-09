---
title: "VsgDbg-Klasse | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg-Klasse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stellt eine Schnittstelle für die programmgesteuerte Kontrolle der In\-App\-Komponente der Grafikdiagnose dar.  
  
## Syntax  
  
```cpp  
class VsgDbg;  
```  
  
## Member  
 Die `VsgDbg`\-Klasse unterstützt die folgenden Member:  
  
### Öffentliche Konstruktoren  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|[VsgDbg::VsgDbg \(Konstruktor\)](../debugger/vsgdbg-vsgdbg-constructor.md)|Erstellt eine Instanz der `VsgDbg`\-Klasse und bereitet optional die In\-App\-Komponente der Grafikdiagnose vor, Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|  
|[VsgDbg::~VsgDbg \(Destruktor\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Zerstört eine Instanz der `VsgDbg`\-Klasse.|  
  
### Öffentliche Methoden  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|[AddMessage](../debugger/addmessage.md)|Fügt dem Grafikdiagnose\-HUD \(Head\-up\-Display\) eine benutzerdefinierte Meldung hinzu.|  
|[BeginCapture](../debugger/begincapture.md)|Startet ein Erfassungsintervall, das mit `EndCapture` endet.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.|  
|[Kopieren \(Programmgesteuerte Aufzeichnung\)](../debugger/copy-programmatic-capture.md)|Kopiert den Inhalt der aktiven Grafikprotokolldatei \(VSGLOG\) in eine neue Datei.|  
|[EndCapture](../debugger/endcapture.md)|Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.|  
|[Init](../debugger/init.md)|Bereitet die In\-App\-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|  
|[ToggleHUD](../debugger/togglehud.md)|Schaltet die Grafikdiagnose\-HUD\-Überlagerung ein oder aus.|  
|[UnInit](../debugger/uninit.md)|Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.|  
  
## Hinweise  
 Die `VsgDbg`\-Klasse stellt eine Schnittstelle dar, die Sie verwenden können, um Grafikdiagnosefunktionen programmgesteuert zu steuern.  Sie können einige Funktionen sogar dann verwenden, wenn Sie Grafikinformationen nicht aktiv erfassen und aufzeichnen. Hierzu gehören die `AddMessage`\-Memberfunktion und die `ToggleHUD`\-Memberfunktion.  Die anderen Memberfunktionen bereiten entweder die In\-App\-Komponente der Grafikdiagnose vor, um die aktive Erfassung von Grafikinformationen zu starten oder zu beenden, oder sie müssen aufgerufen werden, während die App aktiv Grafikinformationen in einer Grafikprotokolldatei erfasst und aufzeichnet.