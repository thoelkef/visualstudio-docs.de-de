---
title: VSG_NODEFAULT_INSTANCE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43affa6db83d34d18a3f485a88f41ccde5d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804411"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert durch das Vorhandensein, ob eine Standardinstanz von die [VsgDbg-Klasse](../debugger/vsgdbg-class.md) Klasse, die die programmgesteuerte erfassungsschnittstelle bereitstellt – angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Wert  
 Ein Präprozessorsymbol, das durch sein Vorhandensein oder seine Abwesenheit bestimmt, ob eine Standardinstanz der `VsgDbg`-Klasse bereitgestellt wird. Wenn dieses Symbol definiert ist, wird keine Standardinstanz der `VsgDbg`-Klasse bereitgestellt. Andernfalls wird eine Standardinstanz bereitgestellt und initialisiert, bevor das Programm ausgeführt wird.  
  
 Die programmgesteuerte Erfassungsschnittstelle wird durch einen Zeiger mit globalem Gültigkeitsbereich bereitgestellt, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Standardinstanz ist häufig ausreichend. Um aber die programmgesteuerte Erfassungsschnittstelle innerhalb einer DLL zu verwenden, wenn das D3D-Gerät außerhalb dieser DLL erstellt wurde, müssen Sie eine eigene Instanz der `VsgDbg`-Klasse erstellen und verwalten. Wenn Sie Ihre eigene Schnittstelle zur programmgesteuerten Erfassungs-API auf diese Weise verwalten, deaktivieren Sie die Standardinstanz, indem Sie `VSG_NODEFAULT_INSTANCE` definieren, um so Mehraufwand zu vermeiden.  
  
 Wenn die Standardinstanz nicht deaktiviert ist, wird sie automatisch initialisiert, bevor Ihr Programm ausgeführt wird, und automatisch zerstört, wenn das Programm endet. Sie müssen diese Instanz nicht explizit initialisieren oder deinitialisieren.  
  
 Um die Standardinstanz zu deaktivieren, müssen Sie definieren `VSG_NODEFAULT_INSTANCE` bevor Sie einfügen `vsgcapture.h` in Ihrem Programm.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt das Deaktivieren der Standardinstanz:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```



