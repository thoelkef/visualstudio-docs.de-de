---
title: Offenlegen von Ereignissen im Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708486"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Verfügbar machen von Ereignissen im Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]können Sie Ereignisse mithilfe der Automatisierung beziehen. Es wird empfohlen, Ereignisse für Projekte und Projektelemente zu beziehen.

 Ereignisse werden von Automatisierungsverbrauchern aus dem <xref:EnvDTE.DTEClass.Events%2A> Objekt abgerufen oder <xref:EnvDTE.DTEClass.GetObject%2A> (z. B. `GetObject("EventObjectName")`). Die Umgebung `IDispatch::Invoke` ruft `DISPATCH_METHOD` mithilfe `DISPATCH_PROPERTYGET` der oder-Flags auf, um ein Ereignis zurückzugeben.

 Im folgenden Prozess wird erläutert, wie VSPackage-spezifische Ereignisse zurückgegeben werden.

1. Die Umgebung beginnt.

2. Es liest aus der Registrierung alle Wertnamen unter den **Schlüsseln Automation**, **AutomationEvents**und **AutomationProperties** aller VSPackages und speichert diese Namen in einer Tabelle.

3. Ein Automatisierungsverbraucher ruft in `DTE.Events.AutomationProjectsEvents` `DTE.Events.AutomationProjectItemsEvents`diesem Beispiel oder auf.

4. Die Umgebung findet den String-Parameter in der Tabelle und lädt das entsprechende VSPackage.

5. Die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> ruft die Methode unter Verwendung des im Aufruf übergebenen Namens auf. in diesem `AutomationProjectsEvents` Beispiel `AutomationProjectItemsEvents`oder .

6. Das VSPackage erstellt ein Stammobjekt `get_AutomationProjectsEvents` mit `get_AutomationProjectItemEvents` Methoden wie und und gibt dann einen IDispatch-Zeiger an das Objekt zurück.

7. Die Umgebung ruft die entsprechende Methode basierend auf dem Namen auf, der an den Automatisierungsaufruf übergeben wird.

8. Die `get_` Methode erstellt ein weiteres IDispatch-basiertes `IConnectionPointContainer` Ereignisobjekt, das sowohl die Schnittstelle als auch die `IConnectionPoint` Schnittstelle implementiert und eine `IDispatchpointer` an das Objekt zurückgibt.

   Um ein Ereignis mithilfe der Automatisierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> verfügbar zu machen, müssen Sie auf die Zeichenfolgen reagieren und darauf achten, die Sie der Registrierung hinzufügen. Im Basic Project-Beispiel sind die Zeichenfolgen *BscProjectsEvents* und *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Registrierungseinträge aus dem Basic Project-Beispiel
 In diesem Abschnitt wird gezeigt, wo der Registrierung Automatisierungsereigniswerte hinzugefügt werden sollen.

 **[HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-Pakete\\<PkgGUID-Automatisierungsereignisse]\>**

 **AutomationProjectEvents** = `AutomationProjectEvents` Gibt das Objekt zurück.

 **AutomationProjectItemEvents** = `AutomationProjectItemsEvents` Gibt das Objekt zurück.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|Standardeinstellung ()|REG_SZ|Nicht verwendet|Nicht verwendet. Sie können das Datenfeld zur Dokumentation verwenden.|
|*AutomationProjectsEvents*|REG_SZ|Name des Ereignisobjekts.|Nur der Schlüsselname ist relevant. Sie können das Datenfeld zur Dokumentation verwenden.<br /><br /> Dieses Beispiel stammt aus dem Beispiel "Basisprojekt".|
|*AutomationProjectItemEvents*|REG_SZ|Name des Ereignisobjekts|Nur der Schlüsselname ist relevant. Sie können das Datenfeld zur Dokumentation verwenden.<br /><br /> Dieses Beispiel stammt aus dem Beispiel "Basisprojekt".|

 Wenn eines Ihrer Ereignisobjekte von einem Automatisierungs-Consumer angefordert wird, erstellen Sie ein Stammobjekt mit Methoden für jedes Ereignis, das Ihr VSPackage unterstützt. Die Umgebung ruft `get_` die entsprechende Methode für dieses Objekt auf. Wenn z. `DTE.Events.AutomationProjectsEvents` B. `get_AutomationProjectsEvents` aufgerufen wird, wird die Methode für das Stammobjekt aufgerufen.

 ![Visual Studio-Projektereignisse](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Automatisierungsmodell für Ereignisse

 Die `CProjectEventsContainer` Klasse stellt das Quellobjekt für `CProjectItemsEventsContainer` *BscProjectsEvents*dar und stellt das Quellobjekt für *BscProjectItemsEvents*dar.

 In den meisten Fällen müssen Sie für jede Ereignisanforderung ein neues Objekt zurückgeben, da die meisten Ereignisobjekte ein Filterobjekt verwenden. Wenn Sie das Ereignis ausdemadien, überprüfen Sie diesen Filter, um sicherzustellen, dass der Ereignishandler aufgerufen wird.

 *AutomationEvents.h* und *AutomationEvents.cpp* enthalten Deklarationen und Implementierungen der Klassen in der folgenden Tabelle.

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|`CAutomationEvents`|Implementiert ein Ereignisstammobjekt, das `DTE.Events` aus dem Objekt abgerufen wird.|
|`CProjectsEventsContainer` und `CProjectItemsEventsContainer`|Implementieren Sie die Ereignisquellobjekte, die die entsprechenden Ereignisse ausfeuern.|

 Das folgende Codebeispiel zeigt, wie sie auf eine Anforderung für ein Ereignisobjekt reagieren.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 Im obigen `g_wszAutomationProjects` Code ist der Name Ihrer Projektsammlung (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) und `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) die Namen von Projektereignissen und Projektelementereignissen, die aus Ihrer VSPackage-Implementierung stammen.

 Ereignisobjekte werden von derselben zentralen `DTE.Events` Position, dem Objekt, abgerufen. Auf diese Weise werden alle Ereignisobjekte gruppiert, sodass ein Endbenutzer nicht das gesamte Objektmodell durchsuchen muss, um ein bestimmtes Ereignis zu finden. Auf diese Weise können Sie auch Ihre spezifischen VSPackage-Objekte bereitstellen, anstatt dass Sie ihren eigenen Code für systemweite Ereignisse implementieren müssen. Für den Endbenutzer, der ein Ereignis `ProjectItem` für Ihre Schnittstelle finden muss, ist jedoch nicht sofort klar, von wo dieses Ereignisobjekt abgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
