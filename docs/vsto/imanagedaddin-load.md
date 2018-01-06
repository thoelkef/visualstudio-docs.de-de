---
title: 'IManagedAddin:: Load | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: 
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 91a2909d407dbdc7629e189585333a3e4702483d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wird aufgerufen, wenn ein verwaltetes VSTO-Add-In geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*bstrManifestURL*|Der vollständige Pfad des Manifests für das VSTO-Add-In.|  
|*pdispApplication*|Ein Zeiger auf eine IDispatch, das die hostanwendung darstellt, die das VSTO-Add-in geladen wird.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt. Beispielsweise kann ein Manifest den Speicherort der VSTO-Add-In-Assembly angeben und die Einstiegspunktklasse instanziieren, wenn das VSTO-Add-In geladen wird.  
  
 Die *BstrManifestURL* Parameter enthält den Wert der `Manifest` -Eintrag unter dem HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<Anwendungsname >*\Addins\\*\<Add-in-ID >* Registrierungsschlüssel für das VSTO-Add-in. Weitere Informationen finden Sie unter [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implementieren Sie die Methode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) , um Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In auszuführen, das geladen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  