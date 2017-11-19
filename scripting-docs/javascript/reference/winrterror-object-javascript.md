---
title: WinRTError-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>WinRTError-Objekt (JavaScript)
Wenn ein Windows-Runtime-Aufruf ein HRESULT zurückgibt, das einen Fehler angibt, wird dieser von JavaScript in einen speziellen Windows-Runtime-Fehler konvertiert. Diese Funktion steht nur in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps zur Verfügung, wenn die Windows-Runtime verfügbar ist (als Teil des globalen JavaScript-Namespace).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Der WinRTError-Fehlertyp wird nur für Fehler verwendet, deren Ursprung in Windows-Runtime-APIs liegt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie ein WinRTError ausgelöst und abgefangen wird.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Methoden  
 Das WinRTError-Objekt hat keine Methoden.  
  
## <a name="properties"></a>Eigenschaften  
 Das WinRTError-Objekt hat die gleichen Eigenschaften wie die [Fehlerobjekt](../../javascript/reference/error-object-javascript.md) Objekt.  
  
## <a name="requirements"></a>Anforderungen  
 Das WinRTError-Objekt wird nur in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps unterstützt, nicht jedoch in Internet Explorer.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)