---
title: Vertrauenseinstellungen für Dateien und Ordner
description: Erfahren Sie, wie Sie Vertrauenseinstellungen für Dateien und Ordner ändern können, um Visual Studio zu schützen.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 08c4b08c33cd954aa427f158158f29cfbe50df94
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384716"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurieren von Vertrauenseinstellungen für Dateien und Ordner

Visual Studio fordert vor dem Öffnen von Projekten, die über das [MOTW](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))-Attribut verfügen, die Benutzergenehmigung. Zur Gewährleistung der erweiterten Sicherheit können Sie Visual Studio auch so konfigurieren, dass die Benutzergenehmigung angefordert wird, noch bevor Dateien oder Ordner geöffnet werden, die über das MOTW-Attribut verfügen oder als *nicht vertrauenswürdig* gekennzeichnet sind. Die Überprüfung von Dateien und Ordnern ist standardmäßig deaktiviert.

> [!WARNING]
> Vor der Genehmigung sollten Sie dennoch sicherstellen, dass die Datei, der Ordner oder die Projektmappe von einer vertrauenswürdigen Person oder einem vertrauenswürdigen Speicherort stammt.

## <a name="configure-trust-settings"></a>Konfigurieren von Vertrauenseinstellungen

Führen Sie die folgenden Schritte aus, um Vertrauenseinstellungen zu ändern:

1. Öffnen Sie **Extras** > **Optionen** > **Vertrauenseinstellungen**, und klicken Sie dann im rechten Bereich auf den Link **Vertrauenseinstellungen konfigurieren**.

2. Wählen Sie die Ebene der Überprüfungen für Dateien und Ordner aus. Für jede Datei bzw. jeden Ordner können Sie verschiedene Überprüfungen einrichten. Folgende Optionen stehen zur Verfügung:

   * **Keine Überprüfung:** Visual Studio führt keine Überprüfungen aus.

   * **MOTW-Attribut überprüfen:** Wenn die Datei oder der Ordner über das MOTW-Attribut verfügt, blockiert Visual Studio den Vorgang und fragt nach der Berechtigung zum Öffnen.

   * **Vertrauenswürdigkeit des Pfads überprüfen:** Wenn die Datei oder der Pfad nicht Teil der Liste **Vertrauenswürdige Pfade** ist, blockiert Visual Studio den Vorgang und fragt nach der Berechtigung zum Öffnen.

   ![Optionen für die Überprüfung der Vertrauenswürdigkeit](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Hinzufügen von vertrauenswürdigen Pfaden

Führen Sie die folgenden Schritte aus, um vertrauenswürdige Pfade hinzuzufügen:

1. Öffnen Sie **Extras** > **Optionen** > **Vertrauenseinstellungen**, und klicken Sie dann im rechten Bereich auf den Link **Vertrauenseinstellungen konfigurieren**.

2. Klicken Sie im Dialogfeld **Vertrauenseinstellungen** auf **Hinzufügen**, und wählen Sie anschließend **Datei** oder **Ordner** aus.

3. Navigieren Sie zu der Datei oder dem Ordner, die bzw. den Sie zur Liste der Vertrauenseinstellungen hinzufügen möchten, und wählen Sie diese aus.

   Der Datei- oder Ordnerpfad wird in der Liste **Vertrauenswürdige Pfade** angezeigt.

   ![Hinzugefügte vertrauenswürdige Pfade](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Entfernen von vertrauenswürdigen Pfaden

Führen Sie die folgenden Schritte aus, um vertrauenswürdige Pfade zu entfernen:

1. Öffnen Sie **Extras** > **Optionen** > **Vertrauenseinstellungen**, und klicken Sie dann im rechten Bereich auf den Link **Vertrauenseinstellungen konfigurieren**.

2. Wählen Sie in der Liste **Vertrauenswürdige Pfade** den Pfad aus, den Sie entfernen möchten, und klicken Sie dann auf **Entfernen**.

   > [!TIP]
   > Halten Sie die **UMSCHALTTASTE** gedrückt, während Sie die Pfade auswählen, um mehrere Einträge auszuwählen.

   Die ausgewählten Pfade werden aus der Liste **Vertrauenswürdige Pfade** entfernt.
