---
title: -Edit („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c4dabbb0c21fd6b4cabb01655485c8158662adb2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667275"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet die angegebene Datei in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argumente  
 `file1`  
 Dies ist optional. Die Datei, die in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geöffnet werden soll. Wenn keine Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vorhanden ist, wird eine neue Instanz mit einem vereinfachten Fensterlayout erstellt, und `file1` wird in dieser neuen Instanz geöffnet.  
  
 `file2`  
 Dies ist optional. Eine oder mehrere zusätzliche Dateien, die in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geöffnet werden sollen.  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn keine Datei angegeben ist und es eine vorhandene Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gibt, wird die vorhandene Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bevorzugt. Wenn keine Datei angegeben ist und es keine Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gibt, wird eine neue Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit einem vereinfachten Fensterlayout erstellt.  
  
 Wenn eine vorhandene Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sich in einem modalen Zustand befindet, zum Beispiel, wenn das [Dialogfeld „Optionen“](../../ide/reference/options-dialog-box-visual-studio.md) offen ist, öffnet sich die Datei in der vorhandenen Instanz, sobald [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sich nicht mehr im modalen Zustand befinden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Datei `MyFile.cs` in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geöffnet, oder die Datei wird in einer neuen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geöffnet, falls noch keine Instanz vorhanden ist.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
