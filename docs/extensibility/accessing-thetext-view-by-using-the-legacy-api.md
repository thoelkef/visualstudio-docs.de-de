---
title: "Zugreifen auf TheText Ansicht über die Legacy-API | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Zugreifen auf TheText Ansicht über die Legacy-API
Eine Textansicht ist eine Darstellung des Texts, der in einem Textpuffer gespeichert ist. Sie können die Textansicht zugreifen, mithilfe der legacy-API, wie im folgenden Abschnitt gezeigt.  
  
## <a name="text-view-object"></a>TextView-Objekt  
 Jede Ansicht eine eigene Textpuffer zugeordnet ist, und die Ansicht ist ein Fenster auf die Daten in den Puffer. Das folgende Diagramm zeigt die wichtigsten Schnittstellen des Text-View-Objekts, der durch dargestellt wird <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Visual Studio-TextView-Objekt](../extensibility/media/vstextview.gif "Vstextview")  
TextView-Objekt  
  
 Die Ansicht ist eine Möglichkeit zum Darstellen von Text in den Puffer. Es enthält Funktionen, z. B. Zeilenumbruch, und gliedern, sodass sehen Sie in der Ansicht keine genaue Darstellung des Texts in den Puffer ist.  
  
 Eine Sicht kann andere Dienste oder Prozesse eingehende Befehle abfangen und entsprechend reagieren, bevor die Ansicht für sie ausgeführt. Der am häufigsten verwendete Dienst zu diesem Zweck wird eine Sprachdienst. Ein Sprachdienst, z. B. müssen möglicherweise den Befehl für die EINGABETASTE, um benutzerdefinierte einrücken Verhalten oder die Tool-Tipps generieren abzufangen.  
  
## <a name="adding-functionality-to-the-text-view"></a>Hinzufügen von Funktionalität zu Textansicht  
 Sie können Text anzeigen Verhalten anpassen, durch die Behandlung von bestimmter Tastatureingaben. Implementieren Sie zum Abfangen von Tastenanschläge <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> für das Objekt, und geben Sie einen Befehlsziel (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) zu überwachen und abzufangen Befehle.  
  
 Textansicht verwendet sequenzielle Architektur für den Befehl Filtern. Neuen Befehlsfilter (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekte) in der Sequenz hinzugefügt werden, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode.  
  
 Ereignisbenachrichtigung für die Textansicht wird bereitgestellt, mit der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` Schnittstelle. Implementieren Sie diese Schnittstelle für das Clientobjekt, um Benachrichtigungen zu Änderungen an der Textansicht. Diese Schnittstelle anzuzeigende Text verfügbar machen, mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle in der Textansicht, um Benachrichtigungen zu Änderungen in der Ansicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Ändern Einstellungen anzeigen, über die Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Verwenden die Text-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)