---
title: "Verweis (Programmgesteuerte Aufzeichnung) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Verweis (Programmgesteuerte Aufzeichnung)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Grafikdiagnose unterstützt die programmgesteuerte Kontrolle über ihre Erfassungsfunktionen durch die programmgesteuerte Erfassungs\-API.  Sie können diese API verwenden, um Meldungen an das Grafikdiagnose\-HUD \(Head\-Up\-Display\) ein\- und auszuschalten und hinzuzufügen, Grafikprotokolldateien zu initialisieren und zu erstellen und Grafikinformationen zu erfassen.  
  
## Programmgesteuerte Erfassungs\-APIs  
  
### Klassen  
  
|Name|Beschreibung|  
|----------|------------------|  
|[VsgDbg\-Klasse](../debugger/vsgdbg-class.md)|Stellt die Schnittstelle dar, durch die die In\-App\-Komponente der Grafikdiagnose programmgesteuert kontrolliert wird.|  
  
### Präprozessorsymbole  
  
|Name|Beschreibung|  
|----------|------------------|  
|[DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.|  
|[VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)|Definiert den Standarddateinamen der Grafikprotokolldatei.|  
|[VSG\_NODEFAULT\_INSTANCE](../debugger/vsg-nodefault-instance.md)|Definiert durch das Vorhandensein, ob eine Standardinstanz der `VsgDbg`\-Klasse bereitgestellt wird.|  
  
## Verwandte Artikel  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Erfassen von Grafikinformationen](../debugger/capturing-graphics-information.md)|Zeigt wie Grafikinformationen aus Ihrer DirectX\-basierten App erfasst werden können, sodass Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Grafikdiagnosetools verwenden können, um Renderingprobleme zu diagnostizieren.|  
|[Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Zeigt, wie die Grafikdiagnose helfen kann, Renderingfehler in DirectX\-Spielen und \-Apps zu debuggen.|