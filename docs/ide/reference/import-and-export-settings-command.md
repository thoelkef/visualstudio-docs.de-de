---
title: "Befehl „Einstellungen importieren und exportieren“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3faa3d77a0aab8edfbe491b9df655931c2f6ed2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="import-and-export-settings-command"></a>Befehl Einstellungen importieren und exportieren
Importiert, exportiert oder setzt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Einstellungen zurück  
  
## <a name="syntax"></a>Syntax  
  
```  
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

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Siehe auch

[Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)  
[Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)