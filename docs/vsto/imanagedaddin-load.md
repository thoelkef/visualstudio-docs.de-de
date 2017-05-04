---
title: "IManagedAddin::Load | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin::Load"
  - "Load-Methode"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  Wird aufgerufen, wenn ein verwaltetes VSTO\-Add\-In geladen wird.  
  
## Syntax  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### Parameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|*bstrManifestURL*|Der vollständige Pfad des Manifests für das VSTO\-Add\-In.|  
|*pdispApplication*|Ein Zeiger auf ein IDispatch\-Element, das die Hostanwendung darstellt, die das VSTO\-Add\-In lädt.|  
  
## Rückgabewert  
 Ein HRESULT\-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## Hinweise  
 Ein Manifest ist eine Datei \(normalerweise eine XML\-Datei\), die Informationen zum Laden des VSTO\-Add\-Ins bereitstellt. Beispielsweise kann ein Manifest den Speicherort der VSTO\-Add\-In\-Assembly angeben und die Einstiegspunktklasse instanziieren, wenn das VSTO\-Add\-In geladen wird.  
  
 Der Parameter *bstrManifestURL* enthält den Wert des `Manifest`\-Eintrags unter dem Registrierungsschlüssel „HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<Anwendungsname\>*\\Addins\\*\<Add\-In\-ID\>*“ für das VSTO\-Add\-In. Weitere Informationen finden Sie unter [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md).  
  
 Implementieren Sie die Methode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md), um Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO\-Add\-In auszuführen, das geladen wird.  
  
## Siehe auch  
 [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  