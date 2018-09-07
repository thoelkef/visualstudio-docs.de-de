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
ms.openlocfilehash: d1ea659d59e780beba3949e7cae363affa312c17
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673720"
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
  
  