---
title: AutoWiederherstellen, Umgebung, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
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
ms.openlocfilehash: 3f6409e31a606fe31fa1296dc937616338f8d62c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943201"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoWiederherstellen, Umgebung, Dialogfeld "Optionen"
Verwenden Sie diese Seite des Dialogfelds „Optionen“, um anzugeben, ob Dateien automatisch gesichert werden sollen oder nicht. Auf dieser Seite können Sie auch angeben, ob modifizierte Dateien wiederhergestellt werden sollen, wenn die integrierte Entwicklungsumgebung (IDE) unerwartet heruntergefahren wird. Sie können auf dieses Dialogfeld zugreifen, indem Sie das Menü **Extras** und anschließend **Optionen** auswählen und dann im Ordner **Umgebung** die Seite **AutoWiederherstellen** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

 **AutoWiederherstellen-Informationen speichern alle \<n> Minuten:** Verwenden Sie diese Option, um anzupassen, wie oft eine Datei automatisch im Editor gespeichert wird. Bei zuvor gespeicherten Dateien wird eine Kopie der Datei in \\...\Eigene Dokumente\Visual Studio\<*version*>\Sicherungsdateien\\<*projektname*> gespeichert. Wenn es sich um eine neue Datei handelt und diese noch nicht manuell gespeichert wurde, wird die Datei automatisch mit einem zufällig generierten Dateinamen gespeichert.

 **Informationen für AutoWiederherstellen beibehalten für \<n> Tage:** Verwenden Sie diese Option, um anzugeben, wie lange Visual Studio Dateien für die automatische Wiederherstellung beibehält.

## <a name="see-also"></a>Siehe auch

- [Optionen (Dialogfeld)](../../ide/reference/options-dialog-box-visual-studio.md)