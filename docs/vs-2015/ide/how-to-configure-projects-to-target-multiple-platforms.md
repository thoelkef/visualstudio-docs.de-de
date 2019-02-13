---
title: 'Vorgehensweise: Konfigurieren von Projekten für mehrere Zielplattformen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e67d4a5df03f128285de45473c933761d6c7eb04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785825"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Gewusst wie: Konfigurieren von Projekten für mehrere Zielplattformen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ermöglicht es, dass eine Projektmappe mehrere verschiedene CPU-Architekturen oder Plattformen auf einmal ansteuert. Auf die Eigenschaften, die für das Festlegen erforderlich sind, kann über das Dialogfeld **Konfigurations-Manager** zugegriffen werden.  
  
## <a name="targeting-a-platform"></a>Ansteuern einer Plattform  
 Mit dem Dialogfeld **Konfigurations-Manager** können Sie Konfigurationen und Plattformen auf Projektmappen- und Projektebene erstellen und festlegen. Jeder Kombination von Konfigurationen und Zielen auf Projektmappenebene können eindeutige Eigenschaften zugeordnet sein. Dadurch können Sie beispielsweise einfach zwischen einer Releasekonfiguration, die eine [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]-Plattform ansteuert, einer Releasekonfiguration, die eine x86-Plattform ansteuert, und einer Debugkonfiguration, die eine x86-Plattform ansteuert, wechseln.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Festlegen der Konfiguration zum Ansteuern einer anderen Plattform  
  
1.  Klicken Sie im Menü **Erstellen** auf **Konfigurations-Manager**.  
  
2.  Wählen Sie im Feld **Aktive Projektmappenplattform** die Plattform aus, die Ihre Projektmappe ansteuern soll, oder klicken Sie auf **\<Neu>**, um eine neue Plattform zu erstellen. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kompiliert Ihre Plattform, damit diese die Plattform ansteuert, die als aktive Plattform im Dialogfeld **Konfigurations-Manager** festgelegt ist.  
  
## <a name="removing-a-platform"></a>Entfernen einer Plattform  
 Wenn Sie feststellen, dass Sie keine Plattform benötigen, können Sie diese mithilfe des Dialogfelds „Konfigurations-Manager“ entfernen. Dadurch werden alle Projektmappen- und Projekteinstellungen entfernt, die Sie für diese Kombination von Konfiguration und Ziel konfiguriert haben.  
  
#### <a name="to-remove-a-platform"></a>Entfernen einer Plattform  
  
1.  Klicken Sie im Menü **Erstellen** auf **Konfigurations-Manager**.  
  
2.  Klicken Sie im Feld **Aktive Projektmappenplattform** auf **\<Bearbeiten>**. Das Dialogfeld **Projektmappenplattformen bearbeiten** wird geöffnet.  
  
3.  Klicken Sie auf die Plattform, die Sie entfernen möchten, und dann auf **Entfernen**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Ansteuern mehrerer Plattformen mit einer Projektmappe  
 Da Sie die Einstellungen basierend auf der Kombination von Konfigurations- und Plattformeinstellungen ändern können, können Sie eine Projektmappe einrichten, die mehr als eine Plattform ansteuern kann.  
  
#### <a name="to-target-multiple-platforms"></a>Ansteuern mehrerer Plattformen  
  
1.  Verwenden Sie den **Konfigurations-Manager**, um mindestens zwei Zielplattformen für die Projektmappe hinzuzufügen.  
  
2.  Wählen Sie die Plattform, die Sie ansteuern möchten, aus der Liste **Aktive Projektmappenplattform** aus.  
  
3.  Erstellen Sie die Projektmappe.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Gleichzeitiges Erstellen von mehreren Projektmappenkonfigurationen  
  
1. Verwenden Sie den **Konfigurations-Manager**, um mindestens zwei Zielplattformen für die Projektmappe hinzuzufügen.  
  
2. Verwenden Sie das Fenster **Batch erstellen**, um mehrere Projektmappenkonfigurationen gleichzeitig zu erstellen.  
  
   Es ist möglich, dass eine Plattform auf Projektebene vorhanden ist, die z.B. auf [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] festgelegt ist, aber keine Projekte innerhalb dieser Projektmappe vorhanden sind, die die gleiche Plattform ansteuern. Es ist ebenfalls möglich, dass mehrere Projekte in Ihrer Projektmappe vorhanden sind, die jeweils unterschiedliche Plattformen ansteuern. Es wird empfohlen, in einer dieser Situationen eine neue Konfiguration mit einem aussagekräftigen Namen zu erstellen, um Verwechselungen zu vermeiden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
