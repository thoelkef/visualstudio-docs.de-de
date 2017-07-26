---
title: "Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: 896da11aa3bc92d153608dc09778817a77eaf7d6
ms.contentlocale: de-de
ms.lasthandoff: 06/23/2017

---
# <a name="how-to-create-and-remove-project-dependencies"></a>Gewusst wie: Erstellen und Entfernen von Projektabhängigkeiten
Beim Erstellen einer Projektmappe, die mehrere Projekte enthält, kann es erforderlich sein, bestimmte Projekte zuerst zu erstellen, um Code zu generieren, der von anderen Projekten verwendet wird. Wenn ein Projekt ausführbaren Code verarbeitet, der von einem anderen Projekt generiert wurde, wird auf das generierende Projekt als Projektabhängigkeit des verarbeitenden Projekts verwiesen. Solche Abhängigkeitsbeziehungen können im Dialogfeld **Projektabhängigkeiten** definiert werden.  

### <a name="to-assign-dependencies-to-projects"></a>So weisen Sie Projekten Abhängigkeiten zu  

1.  Wählen Sie im Projektmappen-Explorer ein Projekt aus.  

2.  Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.  

     Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.  

    > [!NOTE]
    >  Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe mit mehr als einem Projekt verfügbar.  

3.  Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.  

4.  Aktivieren Sie im Feld **Abhängigkeiten** die Kontrollkästchen für alle weiteren Projekte, die vor Erstellung dieses Projekts erstellt werden müssen.  

 Die Projektmappe muss aus mehr als einem Projekt bestehen, bevor Sie Projektabhängigkeiten erstellen können.  

### <a name="to-remove-dependencies-from-projects"></a>So entfernen Sie Abhängigkeiten aus Projekten  

1.  Wählen Sie im Projektmappen-Explorer ein Projekt aus.  

2.  Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.  

     Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.  

    > [!NOTE]
    >  Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe mit mehr als einem Projekt verfügbar.  

3.  Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.  

4.  Deaktivieren Sie im Feld **Abhängigkeiten** die Kästchen neben anderen Projekten, die keine Abhängigkeiten dieses Projekts mehr sind.  

## <a name="see-also"></a>Siehe auch  
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)


