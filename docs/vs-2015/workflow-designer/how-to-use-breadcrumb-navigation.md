---
title: 'Gewusst wie: Verwenden der Breadcrumb-Navigation | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659154"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Vorgehensweise: Verwenden der Brotkrümelnavigation
Es gibt drei Hauptmethoden, den Satz von Aktivitäten zu ändern, der in [!INCLUDE[wfd1](../includes/wfd1-md.md)] angezeigt wird:

1. Doppelklicken Sie, um in zu einer untergeordneten Aktivität zu wechseln.

2. Klicken Sie auf eine Schaltfläche auf der Breadcrumb-Leiste, um zu einer Vorgängeraktivität zu navigieren.

3. Erweitern oder reduzieren Sie Aktivitäten.

### <a name="using-breadcrumb-navigation"></a>Verwenden der Brotkrümelnavigation

1. Doppelklicken Sie auf eine Aktivität in [!INCLUDE[wfd2](../includes/wfd2-md.md)], um die Stammaktivität in die betreffende Aktivität zu ändern. Die Aktivität, auf die Sie geklickt haben, wird am Stamm vollständig erweitert, und ihre Vorgänger werden in der Breadcrumb-Leiste angezeigt. Gelegentlich wird dies auch Durchführen von Drillout bzw. Drillinto bei einer Aktivität genannt.

2. Um zu einem Vorgänger der aktuellen Stammaktivität zu navigieren, klicken Sie auf die Aktivität in der Breadcrumb-Leiste.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Erweitern oder Reduzieren einer Aktivität an Ort und Stelle

1. Wenn Sie auf die Chevrons neben einer Aktivität klicken, wird die betreffende Aktivität an Ort und Stelle erweitert bzw. reduziert.

2. Wenn der Erweiterungszustand durch Klicken auf die Schaltfläche geändert wird, dann wird der neue Erweiterungszustand in XAML gespeichert.

    > [!WARNING]
    > Nicht alle Aktivitäten können an Ort und Stelle erweitert werden. Es gibt zwei Fälle, in denen eine Aktivität nicht an Ort und Stelle erweitert werden kann: wenn das übergeordnete Element der Aktivität es nicht zulässt, dass seine untergeordneten Elementen an Ort und Stelle erweitert werden, (Aktivitäten in einem Flussdiagramm können z. B. nicht an Ort und Stelle erweitert werden), und wenn der Aktivitätsdesigner nicht an Ort und Stelle erweitert werden kann. Obwohl kein Aktivitätsdesigner, der in [!INCLUDE[wfd2](../includes/wfd2-md.md)] enthalten ist, das oben beschriebene Verhalten aufweist, können einige benutzerdefinierte Aktivitäten dieses Verhalten zeigen.

### <a name="expanding-all-or-collapsing-all-activities"></a>Erweitern oder Reduzieren aller Aktivitäten

1. Verwenden Sie die Schaltflächen **Alle erweitern** und **alle** reduzieren der Benutzeroberfläche, um alle Aktivitäten unter dem aktuellen Breadcrumb-Stamm zu erweitern oder zu reduzieren. Beachten Sie, dass es sich bei "Alle erweitern" und "Alle reduzieren" um globale Zustände handelt. Dies bedeutet Folgendes: Wenn Sie die Stamm Aktivität mithilfe der Breadcrumb-Navigation ändern, bleibt der Zustand "Alle erweitern" oder "Alle reduzieren" erhalten, bis Sie auf **Wiederherstellen**klicken

2. Nachdem Sie den Zustand "Alle erweitern" oder "Alle reduzieren" angewendet haben, können Sie auf die Schaltfläche **Wiederherstellen** klicken, um den zuvor auf die jeweilige Aktivität angewendeten Zustand zurückzusehen.

    > [!WARNING]
    > Wenn eine Aktivität, z. b. <xref:System.Activities.Statements.Flowchart> , nicht mehr direkt erweitert ist, wird die der Schaltfläche **Alle erweitern** und **alle** reduzieren zugeordnete Funktionalität im **Flussdiagramm** -Designer deaktiviert. [!INCLUDE[crabout](../includes/crabout-md.md)] den **Flussdiagramm** -Designer finden Sie im Abschnitt [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > "Alle erweitern" wirkt sich auch auf die **Switch** -und **trycatch** -Aktivitäts Designer aus. Wenn Sie auf **Alle erweitern**klicken, werden alle switchfälle und alle try/catch/schließlich-Blöcke angezeigt. Wenn Sie auf " **Wiederherstellen** **" oder "** reduzieren" klicken, werden diese Designer auf ihren Standardzustand zurückversetzt, in dem Sie auf einen einzelnen Fall/Block klicken können, um den Inhalt