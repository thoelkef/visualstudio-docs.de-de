---
title: Zugreifen auf die Textansicht mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184949"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Zugreifen auf die Textansicht mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Textansicht ist eine Darstellung des Texts, der in einem Text Puffer gespeichert wird. Sie können auf die Textansicht zugreifen, indem Sie die Legacy-API verwenden, wie im folgenden Abschnitt gezeigt.  
  
## <a name="text-view-object"></a>Text Ansichts Objekt  
 Jede Ansicht ist einem eigenen Text Puffer zugeordnet, und die Ansicht ist ein Fenster der Daten im Puffer. Das folgende Diagramm zeigt die Schlüssel Schnittstellen des Text Ansichts Objekts, das durch dargestellt wird <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Visual Studio-TextView-Objekt](../extensibility/media/vstextview.gif "vstextview beteiligt ist")  
Text Ansichts Objekt  
  
 Die Sicht stellt eine Möglichkeit dar, den Text im Puffer darzustellen. Sie enthält Features wie Zeilenumbruch und Gliederung, sodass das, was in der Ansicht angezeigt wird, keine exakte Darstellung des Texts im Puffer ist.  
  
 Eine Ansicht ermöglicht es anderen Diensten oder Prozessen, eingehende Befehle abzufangen und auf diese zu reagieren, bevor Sie von der Ansicht bearbeitet werden. Der häufigste Dienst hierfür ist ein Sprachdienst. Ein Sprachdienst benötigt möglicherweise z. b. den Befehl für die EINGABETASTE, um benutzerdefiniertes Einzug Verhalten oder Quick Infos bereitzustellen.  
  
## <a name="adding-functionality-to-the-text-view"></a>Hinzufügen von Funktionen zur Text Ansicht  
 Sie können das Verhalten der Textansicht anpassen, indem Sie bestimmte Tastatureingaben verarbeiten. Um die Tastatureingaben abzufangen, implementieren Sie für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> -Objekt und stellen ein Befehls Ziel ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) zum Überwachen und Abfangen von Befehlen bereit.  
  
 Die Textansicht verwendet die sequenzielle Architektur für Befehls Filter. Neue Befehls Filter (- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekte) werden der Sequenz hinzugefügt, indem die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 Die Ereignis Benachrichtigung für die Textansicht wird mithilfe der- `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` Schnittstelle bereitgestellt. Implementieren Sie diese Schnittstelle für das Client Objekt, um Benachrichtigungen über Änderungen an der Textansicht zu erhalten. Machen Sie diese Schnittstelle für die Textansicht verfügbar, indem Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle in der Textansicht verwenden, um Benachrichtigungen über Änderungen aus der Ansicht zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Ansichts Einstellungen mithilfe der Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Überwachen der globalen Einstellungen mit dem Text-Manager](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
