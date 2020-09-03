---
title: AutoWiederherstellen, Umgebung, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660969"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoWiederherstellen, Umgebung, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie diese Seite des Dialogfelds „Optionen“, um anzugeben, ob Dateien automatisch gesichert werden sollen oder nicht. Auf dieser Seite können Sie auch angeben, ob modifizierte Dateien wiederhergestellt werden sollen, wenn die integrierte Entwicklungsumgebung (IDE) unerwartet heruntergefahren wird. Sie können auf dieses Dialogfeld zugreifen, indem Sie das Menü **Extras** und anschließend **Optionen** auswählen und dann im Ordner **Umgebung** die Seite **AutoWiederherstellen** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **AutoRecover-Informationen alle \<n> Minuten speichern** verwenden Sie diese Option, um anzupassen, wie oft eine Datei automatisch im Editor gespeichert wird. Bei zuvor gespeicherten Dateien wird eine Kopie der Datei unter \\ . ..\Eigene Dateien\Visual Studio \<*version*> \backup Files \\ < *ProjectName*> gespeichert. Wenn es sich um eine neue Datei handelt und diese noch nicht manuell gespeichert wurde, wird die Datei automatisch mit einem zufällig generierten Dateinamen gespeichert.

 **AutoRecover-Informationen für \<n> Tage beibehalten** verwenden Sie diese Option, um anzugeben, wie lange Visual Studio Dateien für die AutoRecovery-Speicherung beibehält.

## <a name="see-also"></a>Weitere Informationen
 [Dialog Feld "Optionen"](../../ide/reference/options-dialog-box-visual-studio.md)
