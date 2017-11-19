---
title: Metadaten als Quelle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 118d19a1be813b0488503be86a316ccc82bd7b37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="metadata-as-source"></a>Metadaten als Quelle
Mithilfe von Metadaten als Quelle können Sie Metadaten anzeigen, die als C#-Quellcode in einem schreibgeschützten Puffer auftreten. Dies ermöglicht eine Ansicht der Deklarationen von Typen und Membern (ohne Implementierungen). Sie können Metadaten als Quelle anzeigen, indem Sie den Befehl **Gehe zu Definition** für Typen oder Member ausführen, deren Quellcode nicht in Ihrem Projekt oder Ihrer Projektmappe verfügbar ist.  
  
> [!NOTE]
>  Wenn Sie versuchen, den **Gehe zu Definition** -Befehl für Typen oder Member auszuführen, die als intern gekennzeichnet sind, zeigt die IDE (integrierte Entwicklungsumgebung) ihre Metadaten nicht als Quelle an, unabhängig davon, ob die referenzierende Assembly ein Friend ist oder nicht.  
  
 Sie können Metadaten als Quelle entweder im Code-Editor oder im **Codedefinitionsfenster** anzeigen.  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Anzeigen von Metadaten als Quelle im Code-Editor  
 Wenn Sie den Befehl **Gehe zu Definition** für ein Element ausführen, dessen Quellcode nicht verfügbar ist, wird ein Dokument mit Registerkarten im Code-Editor angezeigt, das eine Ansicht der Metadaten des betreffenden Elements in der Darstellung als Quelle enthält. Der Name des Typs wird auf der Registerkarte des Dokuments angezeigt, gefolgt von **[aus Metadaten]**.  
  
 Wenn Sie beispielsweise den Befehl **Gehe zu Definition** für <xref:System.Console>ausführen, werden Metadaten für <xref:System.Console> im Code-Editor als C#-Quellcode angezeigt, die seiner Deklaration ähnlich sehen, jedoch ohne Implementierung.  
  
 ![Metadaten als Quelle](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Anzeigen von Metadaten als Quelle im Codedefinitionsfenster  
 Wenn das **Codedefinitionsfenster** aktiv oder sichtbar ist, führt die IDE automatisch den Befehl **Gehe zu Definition** für Elemente unter dem Cursor im Code-Editor sowie für Elemente aus, die in der **Klassenansicht** oder im **Objekt-Browser**ausgewählt sind. Wenn der Quellcode für das betreffende Element nicht verfügbar ist, zeigt die IDE die Metadaten des betreffenden Elements als Quelle im **Codedefinitionsfenster** an.  
  
 Wenn Sie beispielsweise Ihren Cursor innerhalb des Worts <xref:System.Console> im Code-Editor platzieren, werden Metadaten für <xref:System.Console> als Quelle im **Codedefinitionsfenster** angezeigt. Die Quelle ähnelt der <xref:System.Console> -Deklaration, jedoch ohne Implementierung.  
  
 Wenn Sie die Deklaration eines Elements sehen möchten, das im **Codedefinitionsfenster** angezeigt wird, klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie dann auf **Gehe zu Definition**.