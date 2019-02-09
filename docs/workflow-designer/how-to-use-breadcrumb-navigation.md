---
title: 'Workflow-Designer – Vorgehensweise: Verwenden der Brotkrümelnavigation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b4856188cb08379649ab7611dceb5b26b55149
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950473"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Vorgehensweise: Verwenden der Brotkrümelnavigation

Es gibt drei Hauptmethoden, um den Satz von Aktivitäten zu ändern, die im Workflow-Designer angezeigt werden:

1.  Doppelklicken Sie, um in zu einer untergeordneten Aktivität zu wechseln.

2.  Klicken Sie auf eine Schaltfläche auf der Breadcrumb-Leiste, um zu einer Vorgängeraktivität zu navigieren.

3.  Erweitern oder reduzieren Sie Aktivitäten.

## <a name="using-breadcrumb-navigation"></a>Verwenden der Brotkrümelnavigation

1.  Doppelklicken Sie auf eine Aktivität von Workflow-Designer, um die Stammaktivität in die betreffende Aktivität zu ändern. Die betreffende Aktivität ist dann am Stamm vollständig erweitert und dessen Vorgänger in der Breadcrumb-Leiste angezeigt werden. Gelegentlich wird dies auch Durchführen von Drillout bzw. Drillinto bei einer Aktivität genannt.

2.  Um zu einem Vorgänger der aktuellen Stammaktivität zu navigieren, klicken Sie auf die Aktivität in der Breadcrumb-Leiste.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Erweitern oder Reduzieren einer Aktivität an Ort und Stelle

1.  Wenn Sie auf die Chevrons neben einer Aktivität klicken, wird die betreffende Aktivität an Ort und Stelle erweitert bzw. reduziert.

2.  Wenn der Erweiterungszustand durch Klicken auf die Schaltfläche geändert wird, dann wird der neue Erweiterungszustand in XAML gespeichert.

    > [!WARNING]
    > Nicht alle Aktivitäten können an Ort und Stelle erweitert werden. Es gibt zwei Fälle, in denen eine Aktivität nicht an Ort und Stelle erweitert werden kann: wenn das übergeordnete Element der Aktivität es nicht zulässt, dass seine untergeordneten Elementen an Ort und Stelle erweitert werden, (Aktivitäten in einem Flussdiagramm können z. B. nicht an Ort und Stelle erweitert werden), und wenn der Aktivitätsdesigner nicht an Ort und Stelle erweitert werden kann. Auch wenn keine der im Workflow-Designer enthalten die Aktivitäts-Designer das zuletzt genannte Verhalten aufweisen, können einige benutzerdefinierten Aktivitäten dieses Verhalten zeigen.

## <a name="expanding-all-or-collapsing-all-activities"></a>Erweitern oder Reduzieren aller Aktivitäten

1.  Verwenden der **alle erweitern** und **alle reduzieren** Schaltflächen auf der Benutzeroberfläche zum Erweitern oder Reduzieren aller Aktivitäten unter der aktuellen Breadcrumb-Stamms. Beachten Sie, dass es sich bei „Alle erweitern“ und „Alle reduzieren“ um globale Zustände handelt. Dies bedeutet, dass beim Ändern der Stammaktivität mithilfe der Breadcrumb-Navigation, die alle erweitern oder reduzieren alle Zustände erhalten bleibt, bis Sie auf **wiederherstellen**.

2.  Nachdem Sie alle eine erweitern angewendet haben oder reduzieren alle Zustände, können Sie klicken die **wiederherstellen** Schaltfläche, um zurück zu wechseln, um anhand des Status für jede Aktivität zuvor angewendeten angezeigt wird.

    > [!WARNING]
    > Wenn eine Aktivität, z. B. <xref:System.Activities.Statements.Flowchart>, hat an Stelle von zu erweitern, die Funktionen zugeordnet sind die **alle erweitern** und **alle reduzieren** Schaltflächen deaktiviert ist, auf die **Flussdiagramm**  Designer. Weitere Informationen zu den **Flussdiagramm** -Designer finden Sie die [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) Thema.

    > [!WARNING]
    > Alle erweitern Außerdem wird einen spezieller Effekt in **Switch** und **TryCatch** Aktivitäts-Designer. Beim Klicken auf **alle erweitern**, werden alle Switch-Fälle und alle Try/Catch/finally-Blöcke angezeigt. Auf **wiederherstellen** oder **alle reduzieren** werden diese Designer auf ihren Standardzustand zurückgesetzt, in dem Sie klicken können einen einzelnen Fall bzw. Block, um seinen Inhalt anzuzeigen.