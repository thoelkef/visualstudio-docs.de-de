---
title: Text Puffer Ereignisse in der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186404"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Textpufferereignisse in der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Text Puffer Objekt gibt mehrere verschiedene Ereignisse aus, die es Ihnen ermöglichen, auf unterschiedliche Situationen zu reagieren.  
  
 Wenn Sie die Legacy-API verwenden, sollten Sie die folgenden Schnittstellen implementieren, um Benachrichtigungen über Änderungen an den Text Puffer zu erhalten. Machen Sie die Schnittstellen für den Text Puffer mithilfe der- `IConnectionPointContainer` Schnittstelle für den Text Puffer verfügbar, um Benachrichtigungen über Zeilen Änderungen aus dem Puffer zu empfangen. Weitere Informationen finden Sie unter Gewusst [wie: Registrieren für Text Puffer Ereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Im Fall von `IVsTextStreamEvents` -oder `IVsTextLinesEvents` -Schnittstellen werden Änderungen entweder in jeweils einer oder zweidimensionalen Koordinaten zurückgegeben.  
  
## <a name="text-buffer-interfaces"></a>Text Puffer Schnittstellen  
 Im folgenden sind die Schnittstellen aufgeführt, die vom Text Puffer Objekt implementiert werden.  
  
|Schnittstelle|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Verbund Aktionen (d. h. Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz von Dokument Daten, die vom Text Puffer verwaltet werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt grundlegende Dienste bereit. wird von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese-und Schreibfunktionen mit zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnellen, streamorientierten, sequenziellen Zugriff auf Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese-und Schreibfunktionen mithilfe eindimensionaler Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Ermöglicht den Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Mit dieser Schnittstelle können Sie Ihre eigenen zufälligen Daten im Puffer speichern, indem Sie eine GUID erstellen und Sie als Schlüssel verwenden.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|  
  
## <a name="text-buffer-event-interfaces"></a>Text Puffer-Ereignis Schnittstellen  
 Im folgenden finden Sie die Schnittstellen für die Ereignis Benachrichtigung für Text Puffer.  
  
|Schnittstelle|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Benachrichtigt Clients, wenn ein neuer Sprachdienst einem Textpuffer zugeordnet wird.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Benachrichtigt Clients, wenn ein Text Puffer initialisiert wird und wenn Änderungen an den Daten im Text Puffer vorgenommen werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Benachrichtigt Clients über Änderungen am zugrunde liegenden Text Puffer in eindimensionalen Koordinaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Benachrichtigt Clients über Änderungen am zugrunde liegenden Text Puffer in zweidimensionalen Koordinaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Benachrichtigt Clients über Änderungen an Benutzerdaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Benachrichtigt Clients über die letzte Commitgeste zum Auslösen des Ereignisses und stellt den Bereich des geänderten Texts bereit. Die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle wird nicht als Antwort auf Befehle zum Rückgängigmachen oder wiederholen ausgelöst. Ereignisse werden nur für Puffer ausgelöst, die über einen rückgängig-Manager verfügen. `IVsPreliminaryTextChangeCommitEvents` wird vor anderen Ereignissen ausgelöst, z. b. einer hübschen Auflistung, um sicherzustellen, dass die anderen Ereignisse den Text nicht ändern, bevor für die Änderungen ein Commit ausgeführt wird. Das VSPackage muss entweder die- `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die- `IVsFinalTextChangeCommitEvents` Schnittstelle überwachen, aber nicht beides.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Benachrichtigt Clients über die letzte Commitgeste zum Auslösen des Ereignisses und stellt den Bereich des geänderten Texts bereit. Die `IVsFinalTextChangeCommitEvents` Schnittstelle wird nicht als Antwort auf Befehle zum Rückgängigmachen oder wiederholen ausgelöst. Ereignisse werden nur für Puffer ausgelöst, die über einen rückgängig-Manager verfügen. `IVsFinalTextChangeCommitEvents` ist nur für die Verwendung durch Sprachdienste oder andere Objekte vorgesehen, die über eine komplette Kontrolle über die Bearbeitung verfügen. Das VSPackage muss entweder die- `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die- `IVsFinalTextChangeCommitEvents` Schnittstelle überwachen, aber nicht beides.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf den Text Puffer mithilfe der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Vorgehensweise: Registrieren für Textpufferereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
