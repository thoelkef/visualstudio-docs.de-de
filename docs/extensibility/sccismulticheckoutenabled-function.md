---
title: SccIsMultiCheckoutEnabled Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccIsMultiCheckoutEnabled
helpviewer_keywords: SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b04cd593bd631ba92545901ff289a9f8ed4f1822
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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