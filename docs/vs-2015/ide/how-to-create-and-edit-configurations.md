---
title: 'Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c507bb2ea6fa231b2b3f3d92cebb3ca78bb4eb5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071199"
---
# <a name="how-to-create-and-edit-configurations"></a>Gewusst wie: Erstellen und Bearbeiten von Konfigurationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es können mehrere Buildkonfigurationen für eine Projektmappe erstellt werden. Zum Beispiel können Sie ein Debugbuild konfigurieren, das von den Testern zum Suchen und Beheben von Problemen verwendet werden kann, und Sie können unterschiedliche Builds konfigurieren, die Sie an verschiedene Kunden verteilen können.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-build-configurations"></a>Erstellen von Buildkonfigurationen  
 Sie können das Dialogfeld **Konfigurations-Manager** zum Auswählen oder Ändern vorhandener Buildkonfigurationen verwenden oder neue erstellen.  
  
#### <a name="to-open-the-configuration-manager-dialog-box"></a>So öffnen Sie das Dialogfeld "Konfigurations-Manager"  
  
- Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die Projektmappe, und wählen Sie dann **Konfigurations-Manager** aus.  
  
  > [!NOTE]
  >  Wenn der Befehl **Konfigurations-Manager** nicht im Kontextmenü angezeigt wird, suchen Sie auf der Menüleiste im Menü **Erstellen**. Wenn der Befehl dort auch nicht angezeigt wird, wählen Sie auf der Menüleiste **Extras**, **Optionen** aus, und erweitern Sie anschließend im linken Bereich des Dialogfelds **Optionen** die Optionen **Projekte und Projektmappen**, **Allgemein**, und aktivieren Sie im rechten Bereich das Kontrollkästchen **Erweiterte Buildkonfigurationen anzeigen**.  
  
   Sie können im Dialogfeld **Konfigurations-Manager** die Dropdownliste **Konfiguration der aktuellen Projektmappe** verwenden, um eine Projektmappen-weite Buildkonfiguration auszuwählen, eine vorhandene zu ändern oder eine neue Konfiguration zu erstellen. Sie können die Dropdownliste **Aktive Projektmappenplattform** verwenden, um die Plattform auszuwählen, auf die die Konfiguration ausgerichtet ist, eine vorhandene zu ändern, oder eine neue Plattform hinzuzufügen. Im Bereich **Projektkontexte** werden die Projekte in der Projektmappe aufgeführt. Für jedes Projekt können Sie eine projektspezifische Konfiguration und Plattform auswählen, vorhandene ändern oder eine neue Konfiguration erstellen bzw. eine neue Plattform hinzufügen. Sie können auch Kontrollkästchen aktivieren, die angeben, ob jedes Projekt bei Verwendung der Projektmappe-weiten Konfiguration zum Erstellen oder Bereitstellen der Projektmappe eingeschlossen wird.  
  
  Nachdem Sie die gewünschte Konfigurationen festgelegt haben, können Sie die für diese Konfigurationen geeigneten Projekteigenschaften festlegen.  
  
#### <a name="to-set-properties-based-on-configurations"></a>So legen Sie auf Konfigurationen basierende Eigenschaften fest  
  
- Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für ein Projekt, und wählen Sie **Eigenschaften** aus.  
  
     Das Fenster **Eigenschaftenseiten** wird geöffnet.  
  
     Sie können Eigenschaften für die Konfigurationen festlegen. Bei einer Releasekonfiguration z. B. können Sie angeben, dass Code bei Erstellung der Projektmappe optimiert wird, und bei einer Debugkonfiguration können Sie angeben, dass das Symbol `DEBUG` für die bedingte Kompilierung enthalten ist. Weitere Informationen zu den Einstellungen für die Eigenschaftenseiten finden Sie unter [Einführung zum Projekt-Designer](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## <a name="creating-and-modifying-project-configurations"></a>Erstellen und Ändern von Projektkonfigurationen  
  
#### <a name="to-create-a-project-configuration"></a>So erstellen Sie eine Projektkonfiguration  
  
1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.  
  
2. Wählen Sie in der Spalte **Projekt** ein Projekt aus.  
  
3. Wählen Sie im Dropdownmenü **Konfiguration** für dieses Projekt die Option **Neu** aus.  
  
     Das Dialogfeld **Neue Projektkonfiguration** wird angezeigt.  
  
4. Geben Sie im Feld **Name** einen Namen für die neue Konfiguration ein.  
  
5. Wenn Sie die Eigenschafteneinstellungen aus einer bereits vorhandenen Projektkonfiguration verwenden möchten, wählen Sie eine Konfiguration aus der Dropdownliste **Copy settings from** (Einstellungen kopieren von) aus.  
  
6. Um gleichzeitig eine Projektmappen-weite Konfiguration zu erstellen, aktivieren Sie das Kontrollkästchen **Create new solution configuration** (Neue Projektmappenkonfigurationen erstellen).  
  
#### <a name="to-rename-a-project-configuration"></a>So benennen Sie eine Projektkonfiguration um  
  
1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.  
  
2. Wählen Sie in der Spalte **Projekt** das Projekt aus, das über die Projektkonfiguration verfügt, die Sie umbenennen möchten.  
  
3. Wählen Sie im Dropdownmenü **Konfiguration** für dieses Projekt die Option **Bearbeiten** aus.  
  
     Das Dialogfeld **Projektkonfigurationen bearbeiten** wird angezeigt.  
  
4. Markieren Sie den Projektkonfigurationsnamen, den Sie ändern möchten.  
  
5. Wählen Sie **Umbenennen** aus, und geben Sie einen neuen Namen ein.  
  
## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Erstellen und Ändern von Projektmappe-weiten Buildkonfigurationen  
  
#### <a name="to-create-a-solution-wide-build-configuration"></a>So erstellen Sie eine Projektmappen-weite Buildkonfiguration  
  
1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.  
  
2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die Option **Neu** aus.  
  
     Das Dialogfeld **Neue Projektmappenkonfiguration** wird angezeigt.  
  
3. Geben Sie im Textfeld **Name** einen Namen für die neue Konfiguration ein.  
  
4. Wenn Sie die Einstellungen aus einer bereits vorhandenen Projektmappenkonfiguration verwenden möchten, wählen Sie eine Konfiguration aus der Dropdownliste **Copy settings from** (Einstellungen kopieren von) aus.  
  
5. Um Projektkonfigurationen gleichzeitig zu erstellen, aktivieren Sie das Kontrollkästchen **Neue Projektkonfigurationen erstellen**.  
  
#### <a name="to-rename-a-solution-wide-build-configuration"></a>So benennen Sie eine Projektmappen-weite Buildkonfiguration um  
  
1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.  
  
2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die Option **Bearbeiten** aus.  
  
     Das Dialogfeld **Projektmappenkonfigurationen bearbeiten** wird angezeigt.  
  
3. Markieren Sie den Namen der umzubenennenden Projektmappenkonfiguration.  
  
4. Wählen Sie **Umbenennen** aus, und geben Sie einen neuen Namen ein.  
  
#### <a name="to-modify-a-solution-wide-build-configuration"></a>So ändern Sie eine Projektmappen-weite Buildkonfiguration  
  
1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.  
  
2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die gesuchte Konfiguration aus.  
  
3. Wählen Sie im Bereich **Projektkontexte** für jedes Projekt die gewünschte **Konfiguration** und **Plattform** aus, und wählen Sie entweder **Erstellen** oder **Bereitstellen** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [NIB: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
