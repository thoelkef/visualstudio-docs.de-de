---
title: Text-Puffer-Ereignisse in der Legacy-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6851d6f3cbf622794dbf817ec42d941c943add52
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316529"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Text-Puffer-Ereignisse in der legacy-API
Das Textpufferobjekt gibt verschiedene Ereignisse, mit die Sie auf den verschiedenen Situationen reagieren können.

 Wenn Sie die legacy-API verwenden, sollten Sie die folgenden Schnittstellen implementieren, zum Empfangen von Benachrichtigungen über Änderungen an den Textpuffer. Schnittstellen verfügbar, die den Puffer mithilfe der `IConnectionPointContainer` Schnittstelle für den Textpuffer zum Empfangen von Benachrichtigungen über Zeile ändert, aus dem Puffer. Weitere Informationen finden Sie unter [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Im Fall von `IVsTextStreamEvents` oder `IVsTextLinesEvents` Schnittstellen, Änderungen in zurückgegeben werden entweder ein- oder zweidimensionalen Koordinaten entsprechend.

## <a name="text-buffer-interfaces"></a>Text-Puffer-Schnittstellen
 Es folgen die von das Textpufferobjekt implementierten Schnittstellen.

|Interface|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von verbundaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz der Dokumentdaten, die vom Textpuffer verwaltet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt die grundlegenden Dienste. wird von vielen Clients verwendet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese- / Schreibzugriff mithilfe der zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Ermöglicht schnelle und Stream-ausgerichteten sequenziellen Zugriff auf Text im Puffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese- / Schreibzugriff mithilfe der eindimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Sie können Ihre eigenen zufällige Daten in den Puffer mit dieser Schnittstelle speichern, indem erstellen eine GUID und diese als Schlüssel verwenden.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|

## <a name="text-buffer-event-interfaces"></a>Text-Puffer Ereignisschnittstellen
 Es folgen die Schnittstellen für die ereignisbenachrichtigung für Text-Puffer.

|Interface|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Benachrichtigt Clients, wenn ein neuer Sprachdienst einem Textpuffer zugeordnet ist.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Benachrichtigt Clients, wenn ein Textpuffer initialisiert wird und Änderungen an Daten im Textpuffer vorgenommen werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Benachrichtigt Clients über Änderungen an der zugrunde liegenden Textpuffer im eindimensionalen Koordinaten.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Benachrichtigt Clients über Änderungen an der zugrunde liegenden Textpuffer im zweidimensionalen Koordinaten.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Benachrichtigt Clients über Änderungen an Benutzerdaten.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Benachrichtigt Clients über die letzte commitgeste zum Auslösen des Ereignisses und stellt den Bereich des geänderten Texts bereit. Die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle wird als Reaktion auf Rückgängig machen bzw. wiederholen die Befehle nicht ausgelöst. Ereignisse werden nur für die Puffer, die einen Rückgängig-Manager ausgelöst. `IVsPreliminaryTextChangeCommitEvents` vor anderen Ereignisse, z. B. Einrückung, ausgelöst wird, um sicherzustellen, dass die anderen Ereignisse den Text nicht geändert werden, bevor die Änderungen ein Commit ausgeführt werden. Das VSPackage muss entweder überwachen die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die `IVsFinalTextChangeCommitEvents` -Schnittstelle, aber nicht beides.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Benachrichtigt Clients über die letzte commitgeste zum Auslösen des Ereignisses und stellt den Bereich des geänderten Texts bereit. Die `IVsFinalTextChangeCommitEvents` Schnittstelle wird als Reaktion auf Rückgängig machen bzw. wiederholen die Befehle nicht ausgelöst. Ereignisse werden nur für die Puffer, die einen Rückgängig-Manager ausgelöst. `IVsFinalTextChangeCommitEvents` Dient zur Verwendung nur durch Sprachdienste oder andere Objekte, die vollständige Kontrolle über bearbeitet haben. Das VSPackage muss entweder überwachen die `IVsPreliminaryTextChangeCommitEvents` Schnittstelle oder die `IVsFinalTextChangeCommitEvents` -Schnittstelle, aber nicht beides.|

## <a name="see-also"></a>Siehe auch

- [Zugriff auf den Textpuffer mithilfe der legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)
- [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)