---
title: 'Vorgehensweise: Ausschließen von Projekten aus einem Buildvorgang | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffa2b0fd8cab35fc73031d3ead8a5803558c2c07
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667941"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Gewusst wie: Ausschließen von Projekten aus einem Buildvorgang
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Projektmappe erstellen, ohne dafür alle darin enthaltenen Projekte erstellen zu müssen. Beispielsweise können Sie ein Projekt ausschließen, das die Erstellung unterbricht. Sie können dann das Projekt erstellen, nachdem Sie die Probleme ermittelt und behoben haben.

 Sie können ein Projekt wie folgt ausschließen:

- Entfernen Sie es temporär aus der aktiven Projektmappenkonfiguration.

- Durch das Erstellen einer Projektmappenkonfiguration, die das Projekt nicht enthält.

  Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).

### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>So entfernen Sie ein Projekt temporär aus der aktiven Projektmappenkonfiguration

1. Wählen Sie auf der Menüleiste die Option **Erstellen**und dann **Konfigurations-Manager**aus.

2. Suchen Sie in der Tabelle **Projektkontexte** nach dem aus dem Build auszuschließenden Projekt.

3. Deaktivieren Sie in der Spalte **Build** das Kontrollkästchen für das Projekt.

4. Wählen Sie die Schaltfläche **Schließen** aus, und erstellen Sie die Projektmappe dann erneut.

### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>So erstellen Sie eine ein Projekt ausschließende Projektmappenkonfiguration

1. Wählen Sie auf der Menüleiste die Option **Erstellen**und dann **Konfigurations-Manager**aus.

2. Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **\<Neu>** aus.

3. Geben Sie im Feld **Name** einen Namen für die Projektmappenkonfiguration ein.

4. Wählen Sie in der Liste **Copy settings from** (Einstellungen kopieren von) die Projektmappenkonfiguration aus, auf der die neue Konfiguration (beispielsweise **Debug**) basieren soll, und wählen Sie dann die Schaltfläche **OK** aus.

5. Deaktivieren Sie im Dialogfeld **Konfigurations-Manager** das Kontrollkästchen in der Spalte **Erstellen** für das Projekt, das Sie ausschließen möchten, und wählen Sie dann die Schaltfläche **Schließen** aus.

6. Stellen Sie auf der Symbolleiste **Standard** sicher, dass es sich bei der neuen Projektmappenkonfiguration um die aktive Konfiguration im Feld **Projektmappenkonfigurationen** handelt.

7. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe neu erstellen** aus.

## <a name="see-also"></a>Siehe auch
 Grundlagen zu [Buildkonfigurationen](../ide/understanding-build-configurations.md) Gewusst [wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md) Gewusst [wie: Erstellen mehrerer Konfigurationen gleichzeitig](../ide/how-to-build-multiple-configurations-simultaneously.md)
