---
title: "Internationale Einstellungen, Umgebung, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "Internationale Einstellungen (Dialogfeld)"
  - "Sprachen, Umgebungseinstellungen"
  - "Optionen (Dialogfeld), internationale Einstellungen"
  - "Sprachen, Angeben der Standardsprache"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Internationale Einstellungen, Umgebung, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auf der Seite „Internationale Einstellungen“ können Sie die Standardsprache ändern, wenn mehrere Sprachversionen der integrierten Entwicklungsumgebung \(Integrated Development Environment, IDE\) auf Ihrem Computer installiert ist.  Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf  **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Internationale Einstellungen** auswählen.  Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.  
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Sprache**  
 Führt alle verfügbaren Sprachen für die installierten Produktsprachversionen auf.  Diese Option ist nur dann verfügbar, wenn mehrere Sprachversionen auf Ihrem Computer installiert sind.  Wenn mehrere Sprachen des Produkts oder eine gemischte Sprachinstallation von Produkten die gleiche Umgebung gemeinsam verwenden, entspricht die Sprachauswahl der **Microsoft Windows\-Sprache**.  
  
> [!CAUTION]
>  In einem System mit mehreren Sprachen hat diese Einstellung keine Auswirkungen auf die Visual C\+\+\-Buildtools \(cl.exe, link.exe, nmake.exe, bscmake.exe und verwandte Dateien\).  Diese Tools verwenden die Version für die zuletzt installierte Sprache, und die Tools für die zuvor installierte Sprache werden überschrieben, da die Visual C\+\+\-Buildtools nicht das DLL\-Satellitenmodell verwenden.  
  
## Siehe auch  
 [Installieren mehrerer Sprachversionen von Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Dialogfeld "Umgebungsoptionen"](../../ide/reference/environment-options-dialog-box.md)