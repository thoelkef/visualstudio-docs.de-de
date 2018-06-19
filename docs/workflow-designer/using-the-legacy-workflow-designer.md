---
title: Verwenden des Legacyworkflow-Designers
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794b52c918eb727fe67d24af209d21403da18475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975467"
---
# <a name="using-the-legacy-workflow-designer"></a>Verwenden des Legacyworkflow-Designers

Die Vorgängerversion Workflow-Designer bereitgestellter von Visual Studio 2010 kann .NET Framework, Version 3.5 oder die WinFX als Ziel verwendet werden.

Zugriff darauf ist möglich durch Aktivieren der **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster. Ist die Standardoption in Visual Studio 2010 **.NET Framework 4** dient zum Erstellen von Windows Workflow Foundation (WF)-Anwendungen, die auf .NET Framework 4 abzielen.

Workflow-Designer bietet eine Möglichkeit zum Erstellen von Windows Workflow Foundation (WF)-Anwendungen, die mithilfe der vertrauten Visual Studio-Benutzeroberfläche grafisch dargestellt. Windows Workflow Foundation (WF)-Anwendungen bestehen aus der genannten Aktivitäten. Um einen Workflow zu erstellen, erstellen Sie Aktivitäten auf der Entwurfsoberfläche ziehen Sie die jeweiligen Aktivitätsdesigner aus **Toolbox** auf die Entwurfsoberfläche.

In der folgenden Tabelle sind die wichtigsten Features von Visual Studio für Windows Workflow Foundation aufgeführt.

|Feature|Beschreibung|
|-------------|-----------------|
|Drag & Drop-Funktionalität für Aktivitäten|Ziehen Sie Aktivitäten aus der **Toolbox** auf die Entwurfsoberfläche zum Erstellen eines Workflows.|
|Eigenschaftenbrowser|Der Standard **Eigenschaften** Fenster in Visual Studio wird verwendet, um die Eigenschaften einer Aktivität zu konfigurieren.|
|Zoom|Das fernglassymbol **Zoomebene** Symbol befindet sich unterhalb der vertikalen Bildlaufleiste auf der rechten Seite der Entwurfsoberfläche angezeigt. Klicken Sie auf das Fernglas, und wählen Sie einen Prozentsatz für den Zoom aus, um die Workflowgrafik zu vergrößern beziehungsweise zu verkleinern. Sie können auch die **Schwenken** Symbol Vergrößerungsglas Cursoroptionen zum Vergrößern und verkleinern.|
|Schwenken|Die **Schwenken** Symbol, ein Kreis mit vier sich kreuzenden und in vier Richtungen weisenden Pfeilen, befindet sich unterhalb der vertikalen Bildlaufleiste auf der rechten Seite der Entwurfsoberfläche direkt unterhalb des Zoom-fernglassymbols. Wenn Sie auf das Schwenksymbol klicken, erscheint ein Popupmenü mit den folgenden Cursoroptionen:<br /><br /> – Der **vergrößern** -lupencursor können Sie vergrößern, indem Sie auf der Entwurfsoberfläche angezeigt.<br />– Der **verkleinern** -lupencursor können Sie verkleinern, indem Sie auf der Entwurfsoberfläche angezeigt.<br />– Der **Navigationstool** -Handcursor können Sie die "greifen" und verschieben Sie die Ansicht eines Workflows in der Entwurfsoberfläche angezeigt.<br />– Der **Standard** -Pfeilcursor können Sie von anderen Cursorn zurück zum Standardpfeilcursor wechseln.|
|Autobildlauf|Wenn Sie über einen umfangreichen Workflow verfügen, möchten Sie möglicherweise eine Aktivität jenseits der sichtbaren Anzeige des Entwurfsoberflächenbereichs ablegen. Visual Studio können Sie das Ziehen einer Aktivität an den Rand der Entwurfsoberfläche angezeigt, die am nächsten gelegenen, in die Aktivität abgelegt werden sollen. Die Entwurfsoberflächenansicht führt einen automatischen Bildlauf in diese Richtung durch.|
|Smarttags|Aktivitäten, die nicht vollständig konfiguriert oder nicht ordnungsgemäß konfiguriert sind, sind mit einem Ausrufezeichensymbol gekennzeichnet. Sie können auf das Symbol klicken, um eine Dropdownliste mit in der Aktivität vorhandenen Konfigurationsanforderungen aufzurufen. Anschließend können Sie die **Eigenschaften** Fenster entsprechend die Aktivität konfigurieren. Wenn alle Eigenschaften für die Aktivität gültig sind, verschwindet das Ausrufezeichensymbol.|

## <a name="see-also"></a>Siehe auch

- [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)