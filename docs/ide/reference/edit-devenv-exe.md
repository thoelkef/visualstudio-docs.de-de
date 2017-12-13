---
title: "-Edit („devenv.exe“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05a43cbe880244da1abbb117d23fd928c60da9b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Öffnet die angegebene Datei in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argumente  
 `file1`  
 Dies ist optional. Die Datei, die in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet werden soll. Wenn keine Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vorhanden ist, wird eine neue Instanz mit einem vereinfachten Fensterlayout erstellt, und `file1` wird in dieser neuen Instanz geöffnet.  
  
 `file2`  
 Dies ist optional. Eine oder mehrere zusätzliche Dateien, die in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn keine Datei angegeben ist und es eine vorhandene Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt, wird die vorhandene Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bevorzugt. Wenn keine Datei angegeben ist und es keine Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt, wird eine neue Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit einem vereinfachten Fensterlayout erstellt.  
  
 Wenn eine vorhandene Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich in einem modalen Zustand befindet, zum Beispiel, wenn das [Dialogfeld „Optionen“](../../ide/reference/options-dialog-box-visual-studio.md) offen ist, öffnet sich die Datei in der vorhandenen Instanz, sobald [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich nicht mehr im modalen Zustand befinden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Datei `MyFile.cs` in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet, oder die Datei wird in einer neuen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet, falls noch keine Instanz vorhanden ist.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)