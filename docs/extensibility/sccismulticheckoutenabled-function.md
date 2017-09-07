---
title: SccIsMultiCheckoutEnabled Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a8c1a00aa923374b7833e83edde4a0d7b5b4b9b6
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled-Funktion
Diese Funktion überprüft, ob die Datenquellen-Steuerelements, das plug-in auf eine Datei Mehrfaches zulässt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 pbMultiCheckout  
 [out] Gibt an, ob es sich bei Mehrfaches für dieses Projekt (ungleich NULL bedeutet, dass Mehrfaches Auschecken unterstützt werden) aktiviert sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Überprüfung war erfolgreich.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE stellt zwei prüft, ob durch mehrere Benutzer gleichzeitig Dateien ausgecheckt werden können. Zunächst muss das Quellcodeverwaltungssystem Mehrfaches unterstützen. Die Datenquellen-Steuerelement-Plug-in kann diese Funktion während der Initialisierung angeben, durch Angeben der `SCC_CAP_MULTICHECKOUT`. Die IDE ruft anschließend eine zweite Überprüfung dieser Funktion können Sie bestimmen, ob das aktuelle Projekt Mehrfaches unterstützt. Wenn Mehrfaches für das ausgewählte Projekt unterstützt werden, gibt die eine erfolgreiche-Plug-in zurück, code, und legt `pbMultiCheckout` zu ungleich Null (`TRUE`) oder `FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
