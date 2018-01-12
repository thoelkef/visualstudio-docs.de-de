---
title: "Threading-Unterstützung in Office | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3383e3767c97efad9177f0e361524137ea5d66a8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="threading-support-in-office"></a>Threading-Unterstützung in Office
  Dieses Thema enthält Informationen wie die threading in der Microsoft Office-Objektmodell unterstützt wird. Die Office-Objektmodell ist nicht threadsicher, aber es ist möglich, arbeiten mit mehreren Threads in einer Office-Projektmappe. Office-Anwendungen sind Component Object Model (COM)-Server. COM ermöglicht Clients, die zum Aufrufen von COM-Server auf beliebigen Threads. Für COM-Servern, die nicht threadsicher sind, bietet COM einen Mechanismus, um gleichzeitige Aufrufe serialisiert, damit nur über einen logischen Thread zu einem beliebigen Zeitpunkt auf dem Server ausgeführt wird. Dieser Mechanismus wird als Singlethread-Apartment (STA)-Modell bezeichnet. Da Aufrufe serialisiert werden, können Aufrufer für Zeiträume blockiert, während der Server ausgelastet ist oder andere Aufrufe in einem Hintergrundthread behandelt wird.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Erforderliche Kenntnisse für die Verwendung von mehreren Threads  
 Um mit mehreren Threads zu arbeiten, benötigen Sie mindestens über Grundkenntnisse der die folgenden Aspekte von multithreading:  
  
-   Windows-APIs  
  
-   COM Multithread-Konzepte  
  
-   Parallelität  
  
-   Synchronisierung  
  
-   Marshalling  
  
 Allgemeine Informationen zum multithreading, finden Sie unter [verwalteten Threading](/dotnet/standard/threading/).  
  
 Office in die wichtigsten im STA ausgeführt wird Grundlegendes zu den Auswirkungen dieser ermöglicht die erfahren, wie mehrere Threads mit Office verwendet.  
  
## <a name="basic-multithreading-scenario"></a>Grundlegende Multithreading Szenario  
 Code in Office-Projektmappen wird immer auf dem Hauptbenutzeroberflächen-Thread ausgeführt. Möglicherweise möchten die Leistung der Anwendung durch einen separaten Task in einem Hintergrundthread ausführen zu glätten. Das Ziel ist bei zwei scheinbar gleichzeitig statt einer Aufgabe, gefolgt von den anderen Tasks was glattere Ausführung (der Hauptgrund zum Verwenden von mehreren Threads) führen soll. Beispielsweise Sie möglicherweise Ihre Ereigniscode im Hauptthread von Excel-Benutzeroberfläche und in einem Hintergrundthread können Sie eine Aufgabe, die Daten von einem Server erfasst und aktualisiert Zellen in der Excel-Benutzeroberfläche mit den Daten vom Server ausführen.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Hintergrundthreads, die an das Objektmodell der Office aufrufen  
 Wenn ein Hintergrundthread auf die Office-Anwendung aufruft, wird der Aufruf automatisch über die STA-Grenze hinweg gemarshallt. Es ist jedoch keine Garantie, dass die Office-Anwendung den Aufruf zum Zeitpunkt, dass der Hintergrundthread vereinfacht verarbeiten kann. Es gibt mehrere Möglichkeiten:  
  
1.  Die Office-Anwendung muss Nachrichten für den Aufruf von haben die Möglichkeit, geben Datapump. Wenn sie auf diese Weise wird konnte Arbeitsprozessen ausgelastet dieser Zeit in Anspruch nehmen.  
  
2.  Wenn einem anderen logischen Thread bereits in das Apartment befindet, kann nicht der neue Thread eingeben. Dies geschieht häufig, wenn Sie ein logischer Thread wechselt in die Office-Anwendung und einen reeentrant-Aufruf an den Aufrufer Apartment setzt. Die Anwendung wird blockiert, bis zu diesem Aufruf zurückgegeben.  
  
3.  Excel kann in einem Zustand sein, sodass er einen eingehenden Anruf nicht sofort verarbeiten kann. Beispielsweise könnte die Office-Anwendung ein modales Dialogfeld anzeigen.  
  
 Für die Möglichkeiten, 2 und 3, COM stellt die [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) Schnittstelle. Wenn der Server implementiert wird, geben Sie alle Aufrufe über die [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) Methode. Möglichkeit 2 werden Aufrufe automatisch zurückgewiesen. Möglichkeit 3 kann der Server den Aufruf, je nach den Umständen zurück. Wenn der Aufruf abgelehnt wird, muss der Aufrufer Vorgehensweise entscheiden. In der Regel wird der Aufrufer implementiert [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), in diesem Fall über die Ablehnung von benachrichtigt werden würde die [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) Methode.  
  
 Allerdings bei Projektmappen mithilfe von Office-Entwicklungstools in Visual Studio erstellt wurden, COM-Interop konvertiert alle abgelehnten Aufrufe an einen <xref:System.Runtime.InteropServices.COMException> ("der Meldungsfilter gibt an, dass die Anwendung ausgelastet ist"). Sie stellen immer ein Objektmodell, rufen Sie in einem Hintergrundthread, müssen Sie diese Ausnahme behandeln vorbereitet sein. Normalerweise bedeutet dies, und wiederholen Sie dann für eine bestimmte Menge an Zeit, und klicken Sie dann ein Dialogfeld angezeigt wird. Allerdings können Sie auch im Hintergrundthread als STA erstellen und dann registrieren ein Nachrichtenfilters für diesen Thread in diesem Fall.  
  
## <a name="starting-the-thread-correctly"></a>Starten des Threads ordnungsgemäß  
 Bei der Erstellung eines neuen STA-Threads werden den Apartmentzustand auf STA festgelegt, bevor Sie den Thread zu starten. Das folgende Codebeispiel veranschaulicht, wie Sie dabei vorgehen:  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Weitere Informationen finden Sie unter [verwalteten Threading Best Practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Nicht modale Formulare  
 Ein nicht modales Formular kann einige Art der Interaktion mit der Anwendung, während das Formular angezeigt wird. Interaktion des Benutzers mit dem Formular und das Formular interagiert mit der Anwendung ohne zu schließen. Die Office-Objektmodell unterstützt verwaltete nicht modale Formularen; Sie sollten jedoch nicht in einem Hintergrundthread verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltetes Threading](/dotnet/standard/threading/)  
 [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Verwenden von Threads und Threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  