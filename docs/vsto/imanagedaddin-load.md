---
title: IManagedAddin::Load
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: b5f8e94ebcd0aec8e17cac8d651017ed1565d2ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wird aufgerufen, wenn ein verwaltetes VSTO-Add-In geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```c++
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*bstrManifestURL*|Der vollständige Pfad des Manifests für das VSTO-Add-In.|  
|*pdispApplication*|Ein Zeiger auf eine IDispatch, das die hostanwendung darstellt, die das VSTO-Add-in geladen wird.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt. Beispielsweise kann ein Manifest den Speicherort der VSTO-Add-In-Assembly angeben und die Einstiegspunktklasse instanziieren, wenn das VSTO-Add-In geladen wird.  
  
 Die *BstrManifestURL* Parameter enthält den Wert der `Manifest` Eintrag unter der **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Anwendungsname >_ \Addins\\_\<Add-in-ID >_**  Registrierungsschlüssel für das VSTO-Add-in. Weitere Informationen finden Sie unter [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md).  
  
 Implementieren Sie die Methode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) , um Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In auszuführen, das geladen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  