---
title: "Vorgehensweise: Ausschließen von Projekten aus einem Buildvorgang | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: ab5283e92c8ab4bee74f9d6e3c7ae66e67b7a1e8
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-exclude-projects-from-a-build"></a>Gewusst wie: Ausschließen von Projekten aus einem Buildvorgang
Sie können eine Projektmappe erstellen, ohne dafür alle darin enthaltenen Projekte erstellen zu müssen. Beispielsweise können Sie ein Projekt ausschließen, das die Erstellung unterbricht. Sie können dann das Projekt erstellen, nachdem Sie die Probleme ermittelt und behoben haben.  
  
 Sie können ein Projekt wie folgt ausschließen:  
  
-   Entfernen Sie es temporär aus der aktiven Projektmappenkonfiguration.  
  
-   Erstellen Sie eine Projektmappenkonfiguration, die das Projekt nicht enthält.  
  
 Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>So entfernen Sie ein Projekt temporär aus der aktiven Projektmappenkonfiguration  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen**und dann **Konfigurations-Manager**aus.  
  
2.  Suchen Sie in der Tabelle **Projektkontexte** nach dem aus dem Build auszuschließenden Projekt.  
  
3.  Deaktivieren Sie in der Spalte **Build** das Kontrollkästchen für das Projekt.  
  
4.  Wählen Sie die Schaltfläche **Schließen** aus, und erstellen Sie die Projektmappe dann erneut.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>So erstellen Sie eine ein Projekt ausschließende Projektmappenkonfiguration  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen**und dann **Konfigurations-Manager**aus.  
  
2.  Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **\<Neu>** aus.  
  
3.  Geben Sie im Feld **Name** einen Namen für die Projektmappenkonfiguration ein.  
  
4.  Wählen Sie in der Liste **Copy settings from** (Einstellungen kopieren von) die Projektmappenkonfiguration aus, auf der die neue Konfiguration (beispielsweise **Debug**) basieren soll, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Deaktivieren Sie im Dialogfeld **Konfigurations-Manager** das Kontrollkästchen in der Spalte **Erstellen** für das Projekt, das Sie ausschließen möchten, und wählen Sie dann die Schaltfläche **Schließen** aus.  
  
6.  Stellen Sie auf der Symbolleiste **Standard** sicher, dass es sich bei der neuen Projektmappenkonfiguration um die aktive Konfiguration im Feld **Projektmappenkonfigurationen** handelt.  
  
7.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe neu erstellen** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Gewusst wie: Erstellen mehrerer Konfigurationen gleichzeitig](../ide/how-to-build-multiple-configurations-simultaneously.md)
