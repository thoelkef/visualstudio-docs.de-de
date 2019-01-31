---
title: -Updateconfiguration (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9e058d18c0a7c6d1d3b26a5b379c308d26f790ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783160"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
