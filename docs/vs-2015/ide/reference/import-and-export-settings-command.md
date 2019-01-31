---
title: Befehl „Einstellungen importieren und exportieren“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b6b29179332920197960ebe3be71e5973bdc8fe9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769450"
---
# <a name="import-and-export-settings-command"></a>Befehl Einstellungen importieren und exportieren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Importiert, exportiert oder setzt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Einstellungen zurück  
  
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
 Wenn Sie diesen Befehl ohne Schalter ausführen, wird der Assistent **Einstellungen importieren und exportieren** geöffnet. Weitere Informationen finden Sie unter [Vorgehensweise: Freigeben von Einstellungen zwischen Computern oder Visual Studio-Versionen](http://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Beispiel  
 Der folgende Befehl exportiert die aktuellen Einstellungen in die Datei `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
