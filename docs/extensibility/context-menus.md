---
title: "Kontextmen&#252;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Kontextmenüs"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Kontextmen&#252;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kontextmenüs werden angezeigt, wenn ein Benutzer in einem aktiven Bereich des Clientbereichs und freien Für mit der rechten Maustaste klickt, wenn die rechte Maustaste losgelassen wird.  
  
## Editor\-Kontextmenüs  
 Durch die `ECMD_SHOWCONTEXTMENU`abfängt, kann der Sprachdienst die Kontextmenüs steuern, die im Editor anzeigen.  Zum Anzeigen Kontextmenü besitzen, behandeln Sie diesen Befehl wenn es in <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>übergeben wird.  Wenn Sie diesen Befehl behandeln, zeigt die IDE ein Kontextmenü Standardwert an, der für den Editor bereitgestellt wird.  Sie können den Inhalt des Kontextmenüs in einer einzelnen Marker Basis auch steuern.  Weitere Informationen hierzu finden Sie unter [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md) und [Abfangen von Legacy\-Dienst Sprachbefehle](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## Siehe auch  
 [Entwickeln einer Sprache](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)