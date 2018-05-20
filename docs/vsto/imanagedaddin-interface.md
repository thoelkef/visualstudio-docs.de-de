---
title: IManagedAddin-Schnittstelle
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f29356a3e11634d742d6f6022c35cf8f10871eec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddin-interface"></a>IManagedAddin-Schnittstelle
  Implementieren von IManagedAddin-Schnittstelle, um eine Komponente erstellen, die lädt verwalteten VSTO-Add-ins. Diese Schnittstelle wurde in 2007 Microsoft Office System hinzugefügt.  
  
## <a name="syntax"></a>Syntax  
  
```c++
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
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle enthält die Methoden, die durch die IManagedAddin-Schnittstelle definiert sind.  
  
|name|Beschreibung|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wird aufgerufen, wenn eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In lädt.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wird aufgerufen, direkt bevor eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In entlädt.|  
  
## <a name="remarks"></a>Hinweise  
 Microsoft Office-Anwendungen ab 2007 Microsoft Office System verwenden IManagedAddin-Schnittstelle, um Office VSTO-Add-ins zu laden. Sie können die IManagedAddin-Schnittstelle, um eine eigene VSTO-Add-in-Ladeprogramm erstellen implementieren und zur Laufzeit für verwaltete VSTO-Add-ins, anstatt das VSTO-Add-in-Ladeprogramm (*"VSTOLoader.dll"*) und [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Weitere Informationen finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Wie verwaltete Add-Ins geladen werden  
 Die folgenden Schritte werden beim Start einer Anwendung ausgeführt:  
  
1.  Die Anwendung ermittelt VSTO-Add-Ins, indem sie Einträge unter dem folgenden Registrierungsschlüssel sucht:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Anwendungsname >_ \Addins\**  
  
     Jeder Eintrag unter diesem Registrierungsschlüssel entspricht einer eindeutigen ID des VSTO-Add-Ins. In der Regel ist dies der Name der VSTO-Add-In-Assembly.  
  
2.  Die Anwendung sucht unter dem Eintrag für jedes VSTO-Add-In nach einem `Manifest` -Eintrag.  
  
     Verwaltete VSTO-Add-ins können den vollständigen Pfad eines Manifests im Speichern der `Manifest` Eintrag unter **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Anwendungsname >_ \Addins\\  _\<Add-in-ID >_**. Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt.  
  
3.  Wenn die Anwendung einen `Manifest` -Eintrag findet, versucht sie, eine Ladekomponenten für verwaltete VSTO-Add-Ins zu laden. Die Anwendung wird bei dem Versuch, ein COM-Objekt zu erstellen, die IManagedAddin-Schnittstelle implementiert.  
  
     Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enthält eine VSTO-Add-in-Ladekomponente (*"VSTOLoader.dll"*), oder erstellen Sie eigene durch Implementieren von IManagedAddin-Schnittstelle.  
  
4.  Die Anwendung ruft die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode auf und übergibt den Wert des `Manifest` -Eintrags.  
  
5.  Die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode führt zum Laden des VSTO-Add-Ins erforderliche Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In aus, das geladen wird.  
  
 Weitere Informationen zu den Registrierungsschlüsseln, die Microsoft Office-Anwendungen verwenden, um zu ermitteln und Laden verwalteter VSTO-Add-ins verwenden, finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Hinweise zum Implementieren von IManagedAddin  
 Wenn Sie IManagedAddin implementieren, müssen Sie die DLL registrieren, die die Implementierung enthält, mithilfe der folgenden CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office-Anwendungen verwenden diese CLSID, um das COM-Objekt zu erstellen, das IManagedAddin implementiert.  
  
> [!CAUTION]  
>  Diese CLSID wird auch verwendet, indem *"VSTOLoader.dll"* in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aus diesem Grund Wenn Sie IManagedAddin verwenden, um eine eigene VSTO-Add-in-Lade- und-Laufzeitkomponente zu erstellen, kann nicht zum Bereitstellen der Komponentennamens auf Computern, die VSTO-Add-ins ausgeführt werden, die auf basieren die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz zur nicht verwalteten &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  