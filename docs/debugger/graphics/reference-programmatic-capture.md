---
title: Verweis (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826b399aa0ad0b5a45bc6fd80eb73b555cb3f01c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836347"
---
# <a name="reference-programmatic-capture"></a>Verweis (Programmgesteuerte Aufzeichnung)
Die Grafikdiagnose unterstützt die programmgesteuerte Kontrolle über ihre Erfassungsfunktionen durch die programmgesteuerte Erfassungs-API. Sie können diese API verwenden, um Meldungen an das Grafikdiagnose-HUD (Head-Up-Display) ein- und auszuschalten und hinzuzufügen, Grafikprotokolldateien zu initialisieren und zu erstellen und Grafikinformationen zu erfassen.  

## <a name="programmatic-capture-apis"></a>Programmgesteuerte Erfassungs-APIs  

### <a name="classes"></a>Klassen  

|name|Beschreibung|  
|----------|-----------------|  
|[VsgDbg-Klasse](vsgdbg-class.md)|Stellt die Schnittstelle dar, durch die die In-App-Komponente der Grafikdiagnose programmgesteuert kontrolliert wird.|  

### <a name="preprocessor-symbols"></a>Präprozessorsymbole  

|name|Beschreibung|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definiert den Standarddateinamen der Grafikprotokolldatei.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definiert durch das Vorhandensein, ob eine Standardinstanz der `VsgDbg`-Klasse bereitgestellt wird.|  

## <a name="related-articles"></a>Verwandte Artikel  

| Titel | Beschreibung |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Zeigt wie Grafikinformationen aus Ihrer DirectX-basierten App erfasst werden können, sodass Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Grafikdiagnosetools verwenden können, um Renderingprobleme zu diagnostizieren. |
| [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) | Zeigt, wie die Grafikdiagnose helfen kann, Renderingfehler in DirectX-Spielen und -Apps zu debuggen. |
