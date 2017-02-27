---
title: "Verwenden die Text-Manager zum &#220;berwachen von globaler Einstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Überwachen von globalen Einstellungen"
  - "Editoren [Visual Studio SDK] legacy - Text-manager"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Verwenden die Text-Manager zum &#220;berwachen von globaler Einstellungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie einen Kern des Editors implementieren, müssen Sie die Änderungen überwachen, die den globalen Einstellungen vorgenommen werden, da diese Änderungen möglicherweise die Instanz des Editors auswirken.  Sie können die Änderungen verfolgen, indem Sie Ereignisse überwachen, auf die vom Text Manager ausgelöst werden.  Wenn Sie z. B. angeben, speichert eine globale Einstellung für die Darstellung oder des Verhaltens einer Komponente im Kern des Editors, z. B. seinen Dokumenten, der das angegebene Channeldatenobjekt Manager Text wird und diese Informationen für alle betroffenen Clients.  
  
## Text\-Manager\-Funktionen  
 Der Text Manager löst Ereignisse für einige Einstellungen, z. B. folgendermaßen aus:  
  
-   Ob ein Puffer der Quellcodeverwaltung unterliegt  
  
-   Wie Sie für Benachrichtigungen bei Änderungen zum Registrieren  
  
-   So wird nachverfolgt werden, das Puffern mit bestimmten Ansichten zugeordnet sind  
  
-   Text farbauftrag settings  
  
-   Registerkarte Einstellungen für Leerzeichen  
  
 Einstellungen, die für eine bestimmte Sprache eindeutig sind, werden nicht aus Text Manager verwaltet.  Diese Einstellungen müssen für jeden Sprachdienst verwaltet werden.  
  
 Ereignisbenachrichtigungen für den Text <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> Manager wird von der Schnittstelle bereitgestellt.  Implementieren Sie diese Schnittstelle auf dem Client, dem Objekt zum Behandeln von Ereignissen den Text Manager ausgelöst hat.  Sie registrieren für diese Ereignisse, indem Sie die Schnittstelle im Text <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Manager verwenden.  
  
## Siehe auch  
 [In der Core\-Editor](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/de-de/bdac940d-1f14-4019-a01f-fd0bb3dc7198)