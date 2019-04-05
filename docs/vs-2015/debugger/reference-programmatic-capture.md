---
title: Verweis (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957417"
---
# <a name="reference-programmatic-capture"></a>Verweis (Programmgesteuerte Aufzeichnung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Grafikdiagnose unterstützt die programmgesteuerte Kontrolle über ihre Erfassungsfunktionen durch die programmgesteuerte Erfassungs-API. Sie können diese API verwenden, um Meldungen an das Grafikdiagnose-HUD (Head-Up-Display) ein- und auszuschalten und hinzuzufügen, Grafikprotokolldateien zu initialisieren und zu erstellen und Grafikinformationen zu erfassen.  
  
## <a name="programmatic-capture-apis"></a>Programmgesteuerte Erfassungs-APIs  
  
### <a name="classes"></a>Klassen  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[VsgDbg-Klasse](../debugger/vsgdbg-class.md)|Stellt die Schnittstelle dar, durch die die In-App-Komponente der Grafikdiagnose programmgesteuert kontrolliert wird.|  
  
### <a name="preprocessor-symbols"></a>Präprozessorsymbole  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Definiert den Standarddateinamen der Grafikprotokolldatei.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Definiert durch das Vorhandensein, ob eine Standardinstanz der `VsgDbg`-Klasse bereitgestellt wird.|  
  
## <a name="related-articles"></a>Verwandte Artikel  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Capturing Graphics Information](../debugger/capturing-graphics-information.md)|Zeigt wie Grafikinformationen aus Ihrer DirectX-basierten App erfasst werden können, sodass Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Grafikdiagnosetools verwenden können, um Renderingprobleme zu diagnostizieren.|  
|[Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Zeigt, wie die Grafikdiagnose helfen kann, Renderingfehler in DirectX-Spielen und -Apps zu debuggen.|
