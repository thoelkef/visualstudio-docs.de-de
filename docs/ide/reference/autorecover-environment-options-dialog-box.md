---
title: AutoWiederherstellen, Umgebung, Dialogfeld „Optionen“
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5ad6259ede32304cfe15ef4e79c6b3e56dbd9d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143306"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoWiederherstellen, Umgebung, Dialogfeld „Optionen“

Verwenden Sie diese Seite im Dialogfeld **Optionen**, um anzugeben, ob Dateien automatisch gesichert werden sollen oder nicht. Auf dieser Seite können Sie außerdem angeben, ob geänderte Dateien wiederhergestellt werden sollen, wenn Visual Studio unerwartet beendet wird.

Sie greifen auf dieses Dialogfeld zu, indem Sie im Menü **Extras** auf **Optionen** klicken und dann **Umgebung** > **AutoWiederherstellen** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

**AutoWiederherstellen-Informationen speichern alle [n] Minuten**

Verwenden Sie diese Option, um anzupassen, wie oft eine Datei automatisch im Editor gespeichert wird. Bei zuvor gespeicherten Dateien wird eine Kopie der Datei in *%USERPROFILE%\Documents\Visual Studio \<Version>\Backup Files\\<projectname>* gespeichert. Wenn es sich um eine neue Datei handelt und diese noch nicht gespeichert wurde, wird sie mit einem zufällig generierten Dateinamen automatisch gespeichert.

**Informationen für AutoWiederherstellen beibehalten für [n] Tage**

Verwenden Sie diese Option, um anzugeben, wie lange Visual Studio Dateien für die automatische Wiederherstellung beibehält.

## <a name="see-also"></a>Siehe auch

- [Optionen (Dialogfeld)](../../ide/reference/options-dialog-box-visual-studio.md)