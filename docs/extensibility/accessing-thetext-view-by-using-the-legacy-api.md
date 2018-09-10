---
title: Zugreifen auf TheText Ansicht mit der Legacy-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fe57ab7ef5ac113f1248f89cd62ef5b9ec33ca3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081822"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>Zugriff auf die Textansicht mit der legacy-API
Eine Textansicht ist eine Darstellung des Texts, der in einem Textpuffer gespeichert ist. Sie können die Textansicht zugreifen, mit der legacy-API, wie im folgenden Abschnitt gezeigt.

## <a name="text-view-object"></a>Textansichtsobjekt
 Jede Ansicht eine eigene Textpuffer zugeordnet ist, und die Ansicht ist ein Fenster auf die Daten in den Puffer. Das folgende Diagramm zeigt die wichtigsten Textansichtsobjekt, der durch dargestellt wird-Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Visual Studio-TextView-Objekt](../extensibility/media/vstextview.gif "Vstextview") Textansichtsobjekt

 Die Ansicht ist eine Möglichkeit zum Darstellen von Text im Puffer. Es enthält Features wie z. B. den Zeilenumbruch und Gliederungen, sodass die Daten in der Ansicht keine genaue Darstellung des Texts im Puffer sind.

 Eine Ansicht kann andere Dienste oder Prozesse, die eingehenden Befehle abzufangen und entsprechende Maßnahmen zu ergreifen, bevor die Ansicht auf diesen fungiert. Der am häufigsten verwendete Dienst dazu ist ein Sprachdienst. Ein Sprachdienst, zum Beispiel müssen möglicherweise abfangen, den Befehl für die EINGABETASTE, um benutzerdefinierte einrücken Verhalten oder die Tool-Tipps generieren.

## <a name="add-functionality-to-the-text-view"></a>Hinzufügen von Funktionen bei der Textansicht an
 Sie können die textansichtsverhalten anpassen, indem Sie bestimmte Tastatureingaben zu behandeln. Um die Tastatureingaben abfangen, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> auf das Objekt, und geben Sie ein Befehlsziel (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) überwachen und Abfangen von Befehlen.

 Die Textansicht verwendet sequenzielle Architektur für den Befehl Filtern. Neuen Befehlsfilter (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekte) in der Sequenz hinzugefügt werden, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode.

 Die ereignisbenachrichtigung für die Textansicht wird bereitgestellt, mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> Schnittstelle. Implementieren Sie diese Schnittstelle für das Clientobjekt zum Empfangen von Benachrichtigungen über Änderungen an der Textansicht ein. Diese Schnittstelle die Textansicht verfügbar machen, mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle für die Textansicht zum Empfangen von Benachrichtigungen über Änderungen in der Ansicht.

## <a name="see-also"></a>Siehe auch

- [Ändern der ansichtseinstellungen mithilfe der legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Verwenden Sie den TextManager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)