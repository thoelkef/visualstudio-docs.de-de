---
title: -Updateconfiguration (devenv.exe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31fd7f52ad2be89a3e6a40a76948aea0d8cc8bfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513146"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [- Updateconfiguration (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/updateconfiguration-devenv-exe).  
  
  
Teilt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Pakete auf dem System zusammenzuführen und den MEF-Cache auf Änderungen zu prüfen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] führt diesen Befehl automatisch aus, wenn Sie ein VSIX-Paket installieren. Sie sollten `devenv.exe /updateconfiguration` nach dem Patchen Ihrer Dateien ausführen, damit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] den MEF-Cache aktualisiert. Dadurch können Sie feststellen, ob die Korrektur geeignet ist.  
  
## <a name="example"></a>Beispiel  
 Die folgende Befehlszeile bewirkt, dass [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Pakete auf dem System zusammenführt und den MEF-Cache auf Änderungen prüft.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



