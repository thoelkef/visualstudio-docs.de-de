---
title: Ankündigung der Eigenschaft im Fenster-Auswahl-Überwachung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bb2f2ceb7ed7faa3165f2346a0e0d14de1371166
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514764"
---
# <a name="announcing-property-window-selection-tracking"></a>Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster
Wenn Sie zusammenarbeiten möchten die **Eigenschaften** Fenster oder der **Eigenschaft** -Seiten, z. B. ein Formular, Text oder eine Auswahl, die für die Sie Eigenschaften anzeigen möchten haben Sie vollständige Informationen zur Verwendung müssen Sie Koordinieren Sie die Auswahl. Beispielsweise müssen Sie wissen, ob Sie einfach- oder Mehrfachauswahl verfügen. Dann müssen Sie Ihre Auswahltyp (einzelne oder mehrere) mit der IDE bekanntgeben zu können die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle. Diese Schnittstelle bietet Informationen, die erforderlich sind, durch die **Eigenschaften** Fenster.  
  
### <a name="to-announce-selection-to-the-environment"></a>Auswahl in der Umgebung bekanntgeben zu können  
  
1.  Rufen Sie `QueryInterface` für <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Zu diesem Zweck verwenden Sie den Website-Zeiger an die Ansicht übergeben werden, wenn es erstellt wurde.  
  
    2.  Rufen Sie `QueryService` aus der Ansicht für die `SID_STrackSelection` Service.  
  
         Gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Methode, die jedes Mal, wenn die Auswahl geändert wird, und übergeben einen Zeiger auf ein Objekt, das implementiert <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     Das Auswahlobjekt-Container können einfach- oder Mehrfachauswahl und enthält die Auswahlinformationen in einem `IDispatch` Objekt. Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Methode benachrichtigt den **Eigenschaften** Fenster, das die Auswahl geändert hat. Die **Eigenschaften** Fenster verwendet dann die Objekte auf <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> um zu bestimmen, ob einzelne oder mehrere Auswahlmöglichkeiten aufgetreten sind, und was die Auswahl des eigentlichen Objekts sind.  
  
     Bei Angabe eine Mehrfachauswahl aus, und klicken Sie dann die **Eigenschaften** Fenster sucht die Schnittfläche zwischen allgemeine Eigenschaften für die Objekte. Wenn Sie eine einzelnes Objektauswahl angeben und dann die **Eigenschaften** Fenster zeigt alle Eigenschaften für die ein Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [Eigenschaftenseiten](../extensibility/internals/property-pages.md)