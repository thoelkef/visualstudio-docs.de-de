---
title: Grundlagen der Buildkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d847b560b2dcedcd7b6841eccff17f40016c73fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513128"
---
# <a name="understanding-build-configurations"></a>Grundlagen der Buildkonfiguration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Grundlagen der Buildkonfiguration](https://docs.microsoft.com/visualstudio/ide/understanding-build-configurations).  
  
Sie können verschiedene Konfigurationen der Projektmappen- und Projekteigenschaften speichert, die in unterschiedlichen Arten von Builds verwendet werden können. Konfiguration können mit **Configuration Manager** ausgewählt, geändert oder gelöscht werden. Wählen Sie zum Öffnen in der Menüleiste **Erstellen**, **Configuration Manager** aus, oder geben Sie einfach **Konfiguration** im Feld **Schnellstart** ein. Sie können auch die Liste **Projektmappenkonfigurationen** auf der Symbolleiste **Standard** zum Auswählen einer Konfiguration verwenden, oder Sie öffnen den **Configuration Manager**.  
  
> [!NOTE]
>  Falls auf der Symbolleiste keine Einstellungen für Projektmappenkonfigurationen enthalten sind und Sie nicht auf den **Configuration Manager** zugreifen können, sind möglicherweise [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Entwicklungseinstellungen aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten von Konfigurationen mit aktivierten Visual Basic Developer-Einstellungen](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).  
  
 Standardmäßig sind Debug- und Releasekonfigurationen in Projekten, die mithilfe von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Vorlagen erstellt werden, enthalten. Eine Debugkonfiguration unterstützt das Debuggen einer App, und mit einer Releasekonfiguration wird eine Version der App erstellt, die bereitgestellt werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Sie können zudem benutzerdefinierte Projektmappenkonfigurationen und Projektkonfigurationen erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="solution-configurations"></a>Projektmappenkonfigurationen  
 Mit einer Projektmappenkonfiguration wird festgelegt, wie bestimmte Projekte in der Projektmappe erstellt und bereitgestellt werden. Um eine Projektmappenkonfiguration zu ändern oder eine neue, in **Configuration Manager**, unter **Konfiguration der aktuellen Projektmappe** zu definieren, wählen Sie **Neu** oder **Bearbeiten** aus.  
  
 Jeder Eintrag im Feld **Projektkontexte** in einer Projektmappenkonfiguration stellt ein Projekt der Projektmappe dar. Für jede Kombination von **Konfiguration der aktuellen Projektmappe** und **Aktive Projektmappenplattform** können Sie die Verwendungsart des Projekts festlegen. (Weitere Informationen über Projektmappenplattformen finden Sie unter [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md).)  
  
> [!NOTE]
>  Wenn Sie eine neue Projektmappenkonfiguration definieren und das Kontrollkästchen **Neue Projektkonfigurationen erstellen** aktivieren, weist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die neue Konfiguration allen Projekten automatisch zu. Dem entsprechend wird die neue Plattform von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] allen Projekten automatisch zugewiesen, wenn Sie eine neue Plattformkonfiguration definieren und das Kontrollkästchen **Neue Projektplattformen erstellen** aktivieren. Wenn Sie ein Projekt hinzufügen, das auf neue Plattform ausgerichtet ist, wird diese Plattform in Visual Studio der Liste der Projektmappenplattformen hinzugefügt und allen Projekten zugewiesen.  
>   
>  Sie können die Einstellungen für jedes Projekt weiterhin ändern.  
  
 Die aktive Projektmappenkonfiguration stellt der IDE auch Kontext bereit. Wenn Sie z.B. an einem Projekt arbeiten und in der Konfiguration angegeben ist, dass es für ein mobiles Gerät erstellt wird, werden in der **Toolbox** nur die Elemente angezeigt, die in einem Projekt für ein mobiles Gerät verwendet werden können.  
  
## <a name="project-configurations"></a>Projektkonfigurationen  
 Die Konfiguration und Plattform, auf die ein Projekt ausgerichtet ist, werden zusammen verwendet, um die bei der Erstellung zu verwendenden Eigenschaften festzulegen. Ein Projekt kann für jede Kombination aus Konfiguration und Plattform über einen anderen Satz von Eigenschaftendefinitionen verfügen. Zum Ändern der Eigenschaften eines Projekts können Sie die Eigenschaftenseiten nutzen. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.  
  
 Die konfigurationsabhängigen Eigenschaften in einer Projektkonfiguration können den jeweiligen Anforderungen entsprechend definiert werden. Bei einem bestimmten Build kann beispielsweise festgelegt werden, welche Projektelemente eingeschlossen und welche Ausgabedateien erstellt werden, wo sie gespeichert und wie sie optimiert werden.  
  
 Projektkonfigurationen können erhebliche Unterschiede aufweisen. Beispielsweise können die Merkmale einer Konfiguration angeben, dass die Ausgabedatei auf einen minimalen Bereich optimiert wird, und eine andere Konfiguration gibt möglicherweise an, dass die ausführbare Datei mit Höchstgeschwindigkeit ausgeführt wird.  
  
 Projektkonfigurationen werden individuell vom Projektmappen, und nicht vom Benutzer, gespeichert, sodass sie von einem Team gemeinsam verwendet werden können.  
  
 Obwohl Projektabhängigkeiten von der Konfiguration unabhängig sind, werden nur die Projekte erstellt, die in der aktiven Projektmappenkonfiguration angegeben sind.  
  
## <a name="how-visual-studio-assigns-project-configurations"></a>Zuweisen von Projektkonfigurationen bei Visual Studio  
 Wenn Sie eine neue Projektmappenkonfiguration definieren und keine Einstellungen von einer vorhandenen kopieren, werden in Visual Studio zum Zuweisen standardmäßiger Projektkonfigurationen die folgenden Kriterien angewendet. Die Kriterien werden in der angezeigten Reihenfolge ausgewertet.  
  
1.  Wenn ein Projekte einen Konfigurationsname enthält(*\<<Konfigurationsname> \<Plattformname>*), der genau dem Namen der neuen Projektmappenkonfiguration entspricht, wird diese Konfiguration zugewiesen. In Konfigurationsnamen wird die Groß-/Kleinschreibung nicht beachtet.  
  
2.  Wenn das Projekt über einen Konfigurationsnamen verfügt, in dem der der Namensteil der Konfiguration der neuen Projektmappenkonfiguration entspricht, wird diese Konfiguration unabhängig des Plattformteils zugewiesen.  
  
3.  Gibt es auch danach noch keine Übereinstimmung, wird die erste im Projekt aufgeführte Konfiguration zugewiesen.  
  
## <a name="how-visual-studio-assigns-solution-configurations"></a>Zuweisung von Projektmappenkonfigurationen bei Visual Studio  
 Wenn Sie eine Projektkonfiguration erstellen (indem Sie in **Configuration Manager** im Dropdownmenü der Spalte **Konfiguration** für dieses Projekt die Option **Neu** auswählen) und das Kontrollkästchen **Neue Projektmappenkonfigurationen erstellen** aktivieren, wird in Visual Studio nach einer gleich benannten Projektmappenkonfiguration gesucht, um das Projekt auf jeder davon unterstützten Plattform zu erstellen. In einigen Fällen werden vorhandene Projektmappenkonfigurationen von Visual Studio umbenannt, oder es werden neue definiert.  
  
 In Visual Studio werden die folgenden Kriterien für die Zuweisung von Projektmappenkonfigurationen verwendet.  
  
-   Wenn in einer Projektkonfiguration keine Plattform oder nur eine einzige Plattform angegeben ist, wird entweder eine Projektmappenkonfiguration gesucht, deren Name dem der neuen Projektkonfiguration entspricht, oder es wird eine solche hinzugefügt. Der Standardname dieser Projektmappenkonfiguration enthält keinen Plattformnamen und weist das Format *\<Projektkonfigurationsname>* auf.  
  
-   Wenn von einem Projekt mehrere Plattformen unterstützt werden, wird eine Projektmappenkonfiguration für jede unterstützte Plattform gesucht oder hinzugefügt. Der Name jeder Projektmappenkonfiguration umfasst sowohl den Namen der Projektkonfiguration als auch den Plattformnamen und verfügt über das Format *\<Projektkonfigurationsname> \<Plattformname>*.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)   
 [Referenz zur C/C++-Erstellung](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)   
 [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)



