---
title: Befehl Einstellungen importieren und exportieren
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4119abf74281e3c0dbb2b3d5f3ef472a0527a08f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704586"
---
# <a name="import-and-export-settings-command"></a>Befehl Einstellungen importieren und exportieren
Importiert, exportiert oder setzt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Einstellungen zurück

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Schalter
 /export:`filename`

 Dies ist optional. Exportiert die aktuellen Einstellungen in eine angegebene Datei

 /import:`filename`

 Dies ist optional. Importiert die aktuellen Einstellungen in eine angegebene Datei

 /reset

 Dies ist optional. Setzt die aktuellen Einstellungen zurück

## <a name="remarks"></a>Hinweise

Wenn Sie diesen Befehl ohne Schalter ausführen, wird der Assistent **Einstellungen importieren und exportieren** geöffnet. Weitere Informationen finden Sie unter [Synchronisieren der Einstellungen in Visual Studio](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Beispiel

Der folgende Befehl exportiert die aktuellen Einstellungen in die Datei `MyFile.vssettings`.

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Siehe auch

- [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)