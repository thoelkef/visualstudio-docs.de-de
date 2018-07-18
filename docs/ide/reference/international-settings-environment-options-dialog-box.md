---
title: Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afb07a7cbc591c30ebbe7b281b49b38bfb0c911e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944787"
---
# <a name="international-settings-environment-options-dialog-box"></a>Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"
Auf der Seite „Internationale Einstellungen“ können Sie die Standardsprache ändern, wenn mehrere Sprachversionen der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) auf Ihrem Computer installiert ist. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Internationale Einstellungen** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).


 Die Option **Sprache** führt alle verfügbaren Sprachen für die installierten Produktsprachversionen auf. Diese Option ist nur dann verfügbar, wenn mehrere Sprachversionen auf Ihrem Computer installiert sind. Wenn mehrere Sprachen des Produkts oder eine gemischte Sprachinstallation von Produkten die gleiche Umgebung gemeinsam verwenden, entspricht die Sprachauswahl der **Microsoft Windows-Sprache**.

> [!CAUTION]
> In einem System mit mehreren Sprachen hat diese Einstellung keine Auswirkungen auf die Visual C++-Buildtools (cl.exe, link.exe, nmake.exe, bscmake.exe und verwandte Dateien). Diese Tools verwenden die Version für die zuletzt installierte Sprache. Die Buildtools für die zuvor installierte Sprache werden überschrieben, da die Visual C++-Buildtools nicht das DLL-Satellitenmodell verwenden.


## <a name="see-also"></a>Siehe auch

- [Installieren von Sprachpaketen](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)