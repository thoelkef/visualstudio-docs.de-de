---
title: Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cf9fc547451cd77c6f1fff568202f930540f9f1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951708"
---
# <a name="international-settings-environment-options-dialog-box"></a>Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"

Auf der Seite „Internationale Einstellungen“ können Sie die Standardsprache ändern, wenn mehrere Sprachversionen der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) auf Ihrem Computer installiert ist. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Internationale Einstellungen** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

**Sprache**

Führt alle verfügbaren Sprachen für die installierten Produktsprachversionen auf. Diese Option ist nur dann verfügbar, wenn mehrere Sprachversionen auf Ihrem Computer installiert sind. Wenn mehrere Sprachen des Produkts oder eine gemischte Sprachinstallation von Produkten die gleiche Umgebung gemeinsam verwenden, entspricht die Sprachauswahl der **Microsoft Windows-Sprache**.

> [!CAUTION]
> In einem System mit mehreren Sprachen hat diese Einstellung keine Auswirkungen auf die Visual C++-Buildtools (cl.exe, link.exe, nmake.exe, bscmake.exe und verwandte Dateien). Diese Tools verwenden die Version für die zuletzt installierte Sprache. Die Buildtools für die zuvor installierte Sprache werden überschrieben, da die Visual C++-Buildtools nicht das DLL-Satellitenmodell verwenden.

## <a name="see-also"></a>Siehe auch

- [Installieren von Sprachpaketen](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)