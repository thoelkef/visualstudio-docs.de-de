---
title: Ankündigen der Auswahl Nachverfolgung für das Eigenschaften Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002456"
---
# <a name="announcing-property-window-selection-tracking"></a>Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster
Wenn Sie mit dem **Eigenschaften** Fenster oder den Eigenschaften Seiten arbeiten möchten, z. b. einem Formular, Text oder einer Auswahl, für die Sie Eigenschaften anzeigen möchten, müssen Sie über vollständige Kenntnisse **über die Koordinaten** Auswahl verfügen. Sie müssen z. b. wissen, ob Sie eine einzelne Auswahl oder mehrere Auswahlmöglichkeiten haben. Sie müssen dann mithilfe der-Schnittstelle ihren Auswahltyp (einzeln oder mehrere) der IDE ankündigen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . Diese Schnittstelle stellt Informationen bereit, die für das Fenster **Eigenschaften** erforderlich sind.  
  
### <a name="to-announce-selection-to-the-environment"></a>So kündigen Sie die Auswahl für die Umgebung an  
  
1. Wird `QueryInterface` für aufgerufen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Verwenden Sie hierzu den Website Zeiger, der bei seiner Erstellung an die Ansicht übermittelt wurde.  
  
    2. Ruft `QueryService` aus der-Sicht für den `SID_STrackSelection` Dienst auf.  
  
         Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Auswahl geändert wird, wird die-Methode aufgerufen, und es wird ein Zeiger auf ein Objekt übergeben, das implementiert <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     Das Auswahl Container Objekt kann entweder eine einzelne oder mehrere Auswahlmöglichkeiten verwenden und die Auswahl Informationen in einem- `IDispatch` Objekt enthalten. Durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Methode wird das **Eigenschaften** Fenster benachrichtigt, dass sich die Auswahl geändert hat. Das **Eigenschaften** Fenster verwendet dann die-Objekte auf, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> um zu bestimmen, ob eine einzelne oder mehrere Auswahl aufgetreten sind und was die tatsächliche Objektauswahl ist.  
  
     Wenn Sie eine Mehrfachauswahl angeben, wird im **Eigenschaften** Fenster die Schnittmenge zwischen allgemeinen Eigenschaften für die Objekte ermittelt. Wenn Sie eine einzelne Objektauswahl angeben, werden im Fenster **Eigenschaften** alle Eigenschaften für das Objekt angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [Eigenschaftenseiten](../extensibility/internals/property-pages.md)