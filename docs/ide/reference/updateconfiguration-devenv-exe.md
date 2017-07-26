---
title: -Updateconfiguration (devenv.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6e74ef38969cb62790629b34041ceef535ff6f9e
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
Teilt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Pakete auf dem System zusammenzuführen und den MEF-Cache auf Änderungen zu prüfen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] führt diesen Befehl automatisch aus, wenn Sie ein VSIX-Paket installieren. Sie sollten `devenv.exe /updateconfiguration` nach dem Patchen Ihrer Dateien ausführen, damit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den MEF-Cache aktualisiert. Dadurch können Sie feststellen, ob die Korrektur geeignet ist.  
  
## <a name="example"></a>Beispiel  
 Die folgende Befehlszeile bewirkt, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Pakete auf dem System zusammenführt und den MEF-Cache auf Änderungen prüft.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
