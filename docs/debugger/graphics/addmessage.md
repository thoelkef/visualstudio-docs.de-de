---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473347"
---
# <a name="addmessage"></a>AddMessage
Fügt eine benutzerdefinierte Meldung an das Grafikdiagnose *HUD* (Head-Up-Display).  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szMessage`  
 Die dem HUD hinzuzufügende Meldung.  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die hinzugefügt werden, indem diese Funktion aufgerufen wird.  
  
 Um die HUD eine Meldung hinzugefügt haben, müssen Sie nicht aktiv Grafikinformationen erfasst werden – d. h. eine Nachricht über eine Instanz hinzugefügt werden kann die `VsgDbg` -Klasse, aber die [Init](init.md) Member-Funktion werden keine zuerst aufgerufen werden. Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.