---
title: Sccismulticheckoutenabled-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65641803c1fdcb4645bbc20f6cbc845e5d326689
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200063"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion überprüft, ob das Quellcodeverwaltungs-Plug-in mehrere Auschecken für eine Datei zulässt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pContext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 pbmulticheckout  
 vorgenommen Gibt an, ob mehrere Auschecken für dieses Projekt aktiviert sind (ungleich 0 (null) bedeutet, dass mehrere Auschecken unterstützt werden).  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Die Überprüfung war erfolgreich.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die IDE führt zwei Überprüfungen durch, um zu bestimmen, ob Dateien gleichzeitig von mehr als einem Benutzer ausgecheckt werden können. Zuerst muss das Quell Code Verwaltungssystem mehrere Auscheck Vorgänge unterstützen. Das Quellcodeverwaltungs-Plug-in kann diese Funktion während der Initialisierung angeben, indem angegeben wird `SCC_CAP_MULTICHECKOUT` . Danach ruft die IDE als zweite Überprüfung diese Funktion auf, um zu bestimmen, ob das aktuelle Projekt mehrere Auscheck Vorgänge unterstützt. Wenn mehrere Auscheck Vorgänge für das ausgewählte Projekt unterstützt werden, gibt das Plug-in einen Erfolgs Code zurück und legt auf den Wert ungleich `pbMultiCheckout` 0 ( `TRUE` ) oder fest `FALSE` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
