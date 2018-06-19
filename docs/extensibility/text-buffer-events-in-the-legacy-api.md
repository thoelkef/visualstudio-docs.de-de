---
title: Text-Puffer-Ereignisse in die Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab2812d30c0f02063e9ed3672e9b01855c77da22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143071"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Text-Puffer-Ereignisse in die Legacy-API
Die TextBuffer-Objekt gibt verschiedene Ereignisse, mit die verschiedene Situationen reagieren können.  
  
 Wenn Sie die legacy-API verwenden, sollten Sie die folgenden Schnittstellen implementieren, um Benachrichtigungen zu Änderungen an den Textpuffer. Bereitstellen von Schnittstellen, mit dem Text-Puffer mithilfe der `IConnectionPointContainer` Schnittstelle im Text-Puffer zum Empfangen von Benachrichtigungen zu Zeile ändert, aus dem Puffer. Weitere Informationen finden Sie unter [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Im Fall von `IVsTextStreamEvents` oder `IVsTextLinesEvents` Schnittstellen, Änderungen in zurückgegeben werden entweder ein- oder zweidimensionalen Koordinaten, bzw.  
  
## <a name="text-buffer-interfaces"></a>Text-Puffer-Schnittstellen  
 Es folgen die von der TextBuffer-Objekt implementierten Schnittstellen.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von zusammengesetzten Aktivitäten (Aktivitäten, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert werden).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Aktiviert die Persistenz der Dokumentdaten, die von den Textpuffer verwaltet werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt grundlegende Dienste; von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese- / Funktionen, die mit einem zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnelle streamorientiertes, sequenziellen Zugriff auf den Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese- / Funktionen, die über eindimensionale Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder der Moniker des Puffers. Sie können Ihren eigenen zufälligen Daten in den Puffer mit dieser Schnittstelle speichern, indem eine GUID erstellen und verwenden es als Schlüssel.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt die Verbindungspunkte für Ereignisse.|  
  
## <a name="text-buffer-event-interfaces"></a>Text-Puffer Ereignisschnittstellen  
 Im folgenden werden die Schnittstellen für die ereignisbenachrichtigung für Text-Puffer.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Benachrichtigt Clients, wenn ein neue Sprachdienst mit einem Textpuffer zugewiesen wird.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Benachrichtigt Clients, wenn Sie ein Textpuffer initialisiert ist und bei an Daten in den Textpuffer Änderungen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Benachrichtigt Clients über Änderungen an der zugrunde liegenden Textpuffer in eindimensionale Koordinaten an.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Benachrichtigt Clients über Änderungen an der zugrunde liegenden Textpuffer in einem zweidimensionalen Koordinaten an.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Benachrichtigt Clients über Änderungen an Benutzerdaten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Benachrichtigt Clients, der dem letzten Commit-Geste zum Auslösen des Ereignisses, und stellt den Bereich des geänderten Texts. Die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle wird nicht als Antwort auf Rückgängig machen bzw. Wiederholen Befehle ausgelöst. Ereignisse ausgelöst werden nur für die Puffer, die einen Rollback-Manager haben. `IVsPreliminaryTextChangeCommitEvents` vor der anderen Ereignisse, z. B. Einrückung, ausgelöst wird, um sicherzustellen, dass die anderen Ereignisse bevor die Änderungen festgeschrieben werden nicht den Text ändern. Das VSPackage muss entweder überwachen die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die `IVsFinalTextChangeCommitEvents` -Schnittstelle, aber nicht beides.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Benachrichtigt Clients, der dem letzten Commit-Geste zum Auslösen des Ereignisses, und stellt den Bereich des geänderten Texts. Die `IVsFinalTextChangeCommitEvents` Schnittstelle wird nicht als Antwort auf Rückgängig machen bzw. Wiederholen Befehle ausgelöst. Ereignisse ausgelöst werden nur für die Puffer, die einen Rollback-Manager haben. `IVsFinalTextChangeCommitEvents` Dient zur Verwendung nur durch Sprachdienste oder andere Objekte, die vollständige über bearbeiten Kontrolle. Das VSPackage muss entweder überwachen die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die `IVsFinalTextChangeCommitEvents` -Schnittstelle, aber nicht beides.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf den Textpuffer mithilfe der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)