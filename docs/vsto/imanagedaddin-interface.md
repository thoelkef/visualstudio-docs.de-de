---
title: "IManagedAddin-Schnittstelle | Microsoft Docs"
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
  - "IManagedAddin-Schnittstelle"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# IManagedAddin-Schnittstelle
  Implementieren Sie die IManagedAddin\-Schnittstelle zum Erstellen einer Komponente, die verwaltete VSTO\-Add\-Ins lädt. Diese Schnittstelle wurde in 2007 Microsoft Office System hinzugefügt.  
  
## Syntax  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Methoden  
 In der folgenden Tabelle sind die Methoden aufgeführt, die durch die IManagedAddin\-Schnittstelle definiert werden.  
  
|Name|Beschreibung|  
|----------|------------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wird aufgerufen, wenn eine Microsoft Office\-Anwendung ein verwaltetes VSTO\-Add\-In lädt.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wird aufgerufen, direkt bevor eine Microsoft Office\-Anwendung ein verwaltetes VSTO\-Add\-In entlädt.|  
  
## Hinweise  
 Microsoft Office\-Anwendungen ab 2007 Microsoft Office System verwenden die IManagedAddin\-Schnittstelle, um das Laden von Office VSTO\-Add\-Ins zu unterstützen. Sie können die IManagedAddin\-Schnittstelle implementieren, um ein eigenes Ladeprogramm und eine eigene Laufzeit für verwaltete VSTO\-Add\-Ins zu erstellen, anstatt das VSTO\-Add\-In\-Ladeprogramm \(VSTOLoader.dll\) und [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zu verwenden. Weitere Informationen finden Sie unter [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## Wie verwaltete Add\-Ins geladen werden  
 Die folgenden Schritte werden beim Start einer Anwendung ausgeführt:  
  
1.  Die Anwendung ermittelt VSTO\-Add\-Ins, indem sie Einträge unter dem folgenden Registrierungsschlüssel sucht:  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<Anwendungsname\>*\\Addins\\  
  
     Jeder Eintrag unter diesem Registrierungsschlüssel entspricht einer eindeutigen ID des VSTO\-Add\-Ins. In der Regel ist dies der Name der VSTO\-Add\-In\-Assembly.  
  
2.  Die Anwendung sucht unter dem Eintrag für jedes VSTO\-Add\-In nach einem `Manifest`\-Eintrag.  
  
     Verwaltete VSTO\-Add\-Ins können den vollständigen Pfad eines Manifests im `Manifest`\-Eintrag unter "HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<Anwendungsname\>*\\Addins\\*\<Add\-In\-ID\>*" speichern. Ein Manifest ist eine Datei \(normalerweise eine XML\-Datei\), die Informationen zum Laden des VSTO\-Add\-Ins bereitstellt.  
  
3.  Wenn die Anwendung einen `Manifest`\-Eintrag findet, versucht sie, eine Ladekomponenten für verwaltete VSTO\-Add\-Ins zu laden. Dabei versucht die Anwendung, ein COM\-Objekt zu erstellen, das die IManagedAddin\-Schnittstelle implementiert.  
  
     Eine VSTO\-Add\-In\-Ladekomponente \(VSTOLoader.dll\) ist in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enthalten. Sie können auch eine eigene Komponente erstellen, indem Sie die IManagedAddin\-Schnittstelle implementieren.  
  
4.  Die Anwendung ruft die [IManagedAddin::Load](../vsto/imanagedaddin-load.md)\-Methode auf und übergibt den Wert des `Manifest`\-Eintrags.  
  
5.  Die [IManagedAddin::Load](../vsto/imanagedaddin-load.md)\-Methode führt zum Laden des VSTO\-Add\-Ins erforderliche Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO\-Add\-In aus, das geladen wird.  
  
 Weitere Informationen zu den Registrierungsschlüsseln, die Microsoft Office\-Anwendungen zum Ermitteln und Laden verwalteter VSTO\-Add\-Ins verwenden, finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Anleitung zum Implementieren von IManagedAddin  
 Wenn Sie IManagedAddin implementieren, müssen Sie die DLL, die die Implementierung enthält, mithilfe der folgenden CLSID registrieren:  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Microsoft Office\-Anwendungen verwenden diese CLSID zum Erstellen des COM\-Objekts, das IManagedAddin implementiert.  
  
> [!CAUTION]  
>  Diese CLSID wird auch von "VSTOLoader.dll" in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verwendet. Wenn Sie IManagedAddin zum Erstellen einer eigenen VSTO\-Add\-In\-Lade\- und \-Laufzeitkomponente verwenden, können Sie Ihre Komponente daher nicht auf Computern bereitstellen, auf denen VSTO\-Add\-Ins ausgeführt werden, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] abhängig sind.  
  
## Siehe auch  
 [Referenz zur nicht verwalteten API &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  