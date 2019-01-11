---
title: Threading-Unterstützung in Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48a7ab96b26dc9410eef6977c53af7a3cf4a9841
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857892"
---
# <a name="threading-support-in-office"></a>Threading-Unterstützung in Office
  Dieser Artikel enthält Informationen darüber, wie die threading in Microsoft Office-Objektmodell unterstützt wird. Das Office-Objektmodell ist nicht threadsicher, aber es ist möglich, die Arbeit mit mehreren Threads in einer Office-Projektmappe. Office-Anwendungen sind Component Object Model (COM)-Servern. COM ermöglicht Clients, die zum Aufrufen von COM-Server in beliebigen Threads. Für COM-Server, die nicht threadsicher sind, bietet COM über einen Mechanismus, um gleichzeitige Aufrufe zu serialisieren, sodass nur einen logischen Thread zu einem beliebigen Zeitpunkt auf dem Server ausgeführt wird. Dieser Mechanismus wird als das Singlethread-Apartment (STA)-Modell bezeichnet. Da Aufrufe serialisiert werden, möglicherweise Aufrufer für einen Zeitraum blockiert, während der Server ausgelastet ist oder andere Aufrufe in einem Hintergrundthread behandelt wird.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Erforderliche Kenntnisse für die Verwendung von mehreren threads  
 Um mit mehreren Threads zu arbeiten, benötigen Sie mindestens über grundlegende Kenntnisse in die folgenden Aspekte von multithreading:  
  
- Windows-APIs  
  
- COM Multithread-Konzepte  
  
- Parallelität  
  
- Synchronisierung  
  
- Marshalling  
  
  Allgemeine Informationen zum multithreading finden Sie unter [Managed threading](/dotnet/standard/threading/).  
  
  Office wird in die wichtigsten im STA ausgeführt. Kenntnis der Auswirkungen dieser ermöglicht es, zu verstehen, wie die Verwendung mehrerer Threads in Office.  
  
## <a name="basic-multithreading-scenario"></a>Grundlegende multithreading-Szenario  
 Code in Office-Projektmappen wird immer auf dem Hauptbenutzeroberflächen-Thread ausgeführt. Möglicherweise möchten die Leistung der Anwendung glätten, indem Sie einen gesonderten Task in einem Hintergrundthread ausführen. Das Ziel besteht darin, zwei scheinbar gleichzeitig statt einer Aufgabe, gefolgt von der anderen Aufgaben, die reibungslose Ausführung (der Hauptgrund Verwendung mehrerer Threads) führen soll. Beispielsweise Sie möglicherweise Ihre Ereigniscode im Excel-UI-Hauptthread, und in einem Hintergrundthread können Sie eine Aufgabe, die sammelt Daten von einem Server, und aktualisiert Zellen in der Excel-Benutzeroberfläche mit den Daten auf dem Server, ausführen.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Hintergrundthreads, die in der Office-Objektmodell aufgerufen werden soll.  
 Wenn ein Hintergrundthread der Office-Anwendung aufruft, wird der Aufruf automatisch über die STA-Grenze hinweg gemarshallt. Allerdings besteht keine Garantie, dass die Office-Anwendung den Aufruf zum Zeitpunkt, dass der Hintergrundthread vereinfacht verarbeiten kann. Es gibt mehrere Möglichkeiten:  
  
1. Die Office-Anwendung muss Nachrichten für die Gelegenheit haben, geben den Aufruf senden. Wenn das Programm wird konnte Arbeitsprozessen ausgelastet dies Zeit in Anspruch nehmen.  
  
2. Wenn Sie einen anderen logischen Thread bereits im Apartment vorhanden ist, kann keine der neue Thread eingeben. Dies geschieht häufig, wenn Sie ein logischer Thread wechselt von der Office-Anwendung und anschließend einen reeentrant-Aufruf zurück an den Aufrufer des Apartment. Die Anwendung wird blockiert, Aufrufs warten.  
  
3. Excel kann in einem Zustand sein, dass sie keinen eingehenden Anruf sofort verarbeiten kann. Beispielsweise könnte die Office-Anwendung ein modales Dialogfeld anzeigen.  
  
   Möglichkeiten, 2 und 3, COM stellt die [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) Schnittstelle. Wenn es sich bei der Server implementiert wird, geben Sie alle Aufrufe über die [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) Methode. Möglichkeit, 2 werden die Aufrufe automatisch zurückgewiesen. Möglichkeit, 3 kann der Server den Aufruf, je nach den Umständen zurückweisen. Wenn der Aufruf abgelehnt wird, muss der Aufrufer bei Ihrer Entscheidung. In der Regel implementiert die Aufrufer [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), in diesem Fall über die Ablehnung von nicht benachrichtigt werden sollen die [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) Methode.  
  
   COM-Interop konvertiert jedoch im Fall von Lösungen, die mithilfe von Office-Entwicklungstools in Visual Studio erstellt werden, alle abgelehnten Aufrufe an eine <xref:System.Runtime.InteropServices.COMException> ("der Meldungsfilter gibt an, dass die Anwendung ausgelastet ist."). Jedes Mal, wenn Sie ein Objektmodell, rufen Sie stellen in einem Hintergrundthread, Sie müssen darauf vorbereitet sein, diese Ausnahme zu behandeln. In der Regel umfasst, die für einen bestimmten Zeitraum wiederholen, und klicken Sie dann ein Dialogfeld angezeigt wird. Allerdings können Sie auch erstellen, den Hintergrundthread als STA und einen Nachrichtenfilter für diesen Thread in diesem Fall registriert.  
  
## <a name="start-the-thread-correctly"></a>Der Thread wird korrekt gestartet.  
 Wenn Sie einen neuen STA-Thread erstellen, werden festlegen Sie den Apartmentzustand auf STA, bevor Sie den Thread zu starten. Das folgende Codebeispiel veranschaulicht, wie Sie dabei vorgehen:  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Weitere Informationen finden Sie unter [Managed threading best Practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Nicht modale Formulare  
 Ein nicht modales Formular ermöglicht eine Art von Interaktion mit der Anwendung, während das Formular angezeigt wird. Der Benutzer interagiert mit dem Formular und das Formular interagiert, mit der Anwendung ohne zu schließen. Das Office-Objektmodell unterstützt verwaltete nicht modale Formulare. Sie sollten jedoch nicht in einem Hintergrundthread verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Das verwaltete threading](/dotnet/standard/threading/)  
 [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Verwenden von Threads und threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
