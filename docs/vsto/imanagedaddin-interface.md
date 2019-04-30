---
title: IManagedAddin-Schnittstelle
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 320b20fa40250ca47dd414b362059e152eba2c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420991"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin-Schnittstelle
  Implementieren von IManagedAddin-Schnittstelle, um eine Komponente zu erstellen, die lädt verwaltete VSTO-Add-ins. Diese Schnittstelle wurde in 2007 Microsoft Office System hinzugefügt.

## <a name="syntax"></a>Syntax

```csharp
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
 Die folgende Tabelle enthält die Methoden, die von der IManagedAddin-Schnittstelle definiert sind.

|Name|Beschreibung|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wird aufgerufen, wenn eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In lädt.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wird aufgerufen, direkt bevor eine Microsoft Office-Anwendung ein verwaltetes VSTO-Add-In entlädt.|

## <a name="remarks"></a>Hinweise
 Microsoft Office-Anwendungen ab 2007 Microsoft Office System verwenden die IManagedAddin-Schnittstelle, beim Laden von Office VSTO-Add-ins. Sie können die IManagedAddin-Schnittstelle zum Erstellen Ihrer eigenen VSTO-Add-in-Ladeprogramm implementieren und -Laufzeit für verwaltete VSTO-Add-ins, anstatt das VSTO-Add-in-Ladeprogramm (*"VSTOLoader.dll"*) und [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Weitere Informationen finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Wie verwaltete Add-Ins geladen werden
 Die folgenden Schritte werden beim Start einer Anwendung ausgeführt:

1. Die Anwendung ermittelt VSTO-Add-Ins, indem sie Einträge unter dem folgenden Registrierungsschlüssel sucht:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<application name>* \Addins\\**

    Jeder Eintrag unter diesem Registrierungsschlüssel entspricht einer eindeutigen ID des VSTO-Add-Ins. In der Regel ist dies der Name der VSTO-Add-In-Assembly.

2. Die Anwendung sucht unter dem Eintrag für jedes VSTO-Add-In nach einem `Manifest` -Eintrag.

    Verwaltete VSTO-Add-ins können den vollständigen Pfad eines Manifests im Speichern der `Manifest` Eintrag unter **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Anwendungsname >_ \Addins\\  _\<Add-in-ID >_**. Ein Manifest ist eine Datei (normalerweise eine XML-Datei), die Informationen zum Laden des VSTO-Add-Ins bereitstellt.

3. Wenn die Anwendung einen `Manifest` -Eintrag findet, versucht sie, eine Ladekomponenten für verwaltete VSTO-Add-Ins zu laden. Die Anwendung wird versucht, ein COM-Objekt zu erstellen, die IManagedAddin-Schnittstelle implementiert.

    Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enthält ein VSTO-Add-in-Ladekomponente (*"VSTOLoader.dll"*), oder Sie erstellen Ihre eigenen, indem die IManagedAddin-Schnittstelle implementieren.

4. Die Anwendung ruft die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode auf und übergibt den Wert des `Manifest` -Eintrags.

5. Die [IManagedAddin::Load](../vsto/imanagedaddin-load.md) -Methode führt zum Laden des VSTO-Add-Ins erforderliche Aufgaben wie das Konfigurieren der Anwendungsdomäne und der Sicherheitsrichtlinie für das VSTO-Add-In aus, das geladen wird.

   Weitere Informationen zu den Registrierungsschlüsseln verwalteten Schlüsseln, die Microsoft Office-Anwendungen verwenden, um zu ermitteln und Laden von VSTO-Add-ins, finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Anleitungen zum Implementieren von IManagedAddin
 Wenn Sie IManagedAddin implementieren, müssen Sie die DLL registrieren, die die Implementierung enthält, mithilfe der folgenden CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office-Anwendungen verwenden diese CLSID der COM-Objekt zu erstellen, das IManagedAddin implementiert.

> [!CAUTION]
> Diese CLSID wird auch vom verwendet *"VSTOLoader.dll"* in die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aus diesem Grund bei IManagedAddin zum Erstellen Ihrer eigenen VSTO-Add-in-Ladeprogramm und Runtime-Komponente Verwendung kann nicht zum Bereitstellen der Komponentennamens auf Computern, die VSTO-Add-ins ausgeführt werden, die auf basieren die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="see-also"></a>Siehe auch
- [API-Referenz zur nicht verwalteten &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
