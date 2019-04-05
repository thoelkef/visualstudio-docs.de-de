---
title: AddMessage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f01d4e80c3740ae27b5df8badbc74989c2da2c60
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947061"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fügt dem Grafikdiagnose-*HUD* (Head-Up Display) eine benutzerdefinierte Meldung hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szMessage`  
 Die dem HUD hinzuzufügende Meldung.  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die hinzugefügt werden, indem diese Funktion aufgerufen wird.  
  
 Um dem HUD eine Meldung hinzuzufügen, müssen Sie Grafikinformationen nicht aktiv erfassen – d.h. eine Meldung kann durch eine Instanz der `VsgDbg`-Klasse hinzugefügt werden, die Memberfunktion [Init](../debugger/init.md) muss jedoch nicht zuerst aufgerufen werden. Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.
