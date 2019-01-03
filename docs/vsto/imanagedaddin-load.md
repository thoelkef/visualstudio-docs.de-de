---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67a1f330862ad6156d85a8f86afcfe863d776850
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924448"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wird aufgerufen, wenn ein verwaltetes VSTO-Add-In geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```csharp
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*bstrManifestURL*|Der vollständige Pfad des Manifests für das VSTO-Add-In.|  
|*pdispApplication*|Ein Zeiger auf eine IDispatch, die die hostanwendung darstellt, die das VSTO-Add-in geladen wird.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt. Beispielsweise kann ein Manifest den Speicherort der VSTO-Add-In-Assembly angeben und die Einstiegspunktklasse instanziieren, wenn das VSTO-Add-In geladen wird.  
  
 Die *BstrManifestURL* Parameter enthält den Wert des der `Manifest` Eintrag unter dem **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Anwendungsname >_ \Addins\\_\<Add-in-ID >_**  Registrierungsschlüssel für das VSTO-Add-in. Weitere Informationen finden Sie unter [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md).  
  
 Implementieren Sie die Methode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) , um Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In auszuführen, das geladen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
