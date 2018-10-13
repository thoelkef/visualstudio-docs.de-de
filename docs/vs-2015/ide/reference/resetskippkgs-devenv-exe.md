---
title: -ResetSkipPkgs („devenv.exe“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2345c675f55be5c01ea65f5266d4b73bff30feed
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190362"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Löscht alle Optionen, damit bei Benutzern, die keine problematischen VSPackages laden möchten, das Laden hinzugefügter VSPackages übersprungen wird, und startet dann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Tag „SkipLoading“ deaktiviert das Laden eines VSPackage, während das Leeren des Tags das Laden des VSPackage erneut aktiviert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden alle SkipLoading-Tags geleert.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



