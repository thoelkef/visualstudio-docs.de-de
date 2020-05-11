---
title: Anzeigen von Projektobjekten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708470"
---
# <a name="expose-project-objects"></a>Stellen sie Projektobjekte zur Zeit

Benutzerdefinierte Projekttypen können Automatisierungsobjekte bereitstellen, um den Zugriff auf das Projekt mithilfe von Automatisierungsschnittstellen zu ermöglichen. Von jedem Projekttyp wird <xref:EnvDTE.Project> erwartet, dass er <xref:EnvDTE.Solution>das Standardautomatisierungsobjekt zur Verfügung stellt, auf das von zugegriffen wird, das eine Auflistung aller Projekte enthält, die in der IDE geöffnet sind. Es wird erwartet, dass jedes Element <xref:EnvDTE.ProjectItem> im `Project.ProjectItems`Projekt von einem Objekt verfügbar gemacht wird, auf das mit zugegriffen wird. Zusätzlich zu diesen Standard-Automatisierungsobjekten können Projekte projektspezifische Automatisierungsobjekte anbieten.

Sie können benutzerdefinierte Automatisierungsobjekte auf Stammebene erstellen, auf die `DTE.<customObjectName>` Sie `DTE.GetObject("<customObjectName>")`spät gebunden vom Stamm-DTE-Objekt mit oder zugreifen können. Visual C++ erstellt beispielsweise eine projektspezifische C++-Projektsammlung namens *VCProjects,* auf die Sie mit `DTE.VCProjects` oder `DTE.GetObject("VCProjects")`zugreifen können. Sie können auch `Project.Object`eine erstellen, die für `Project.CodeModel`den Projekttyp eindeutig ist, eine , die `ProjectItem`für das `ProjectItem.Object` am `ProjectItem.FileCodeModel`häufigsten abgeleitete Objekt abgefragt werden kann, und eine , die verfügbar macht, und eine .

Es ist eine allgemeine Konvention für Projekte, eine benutzerdefinierte, projektspezifische Projektsammlung verfügbar zu machen. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Erstellt z. B. eine C++-spezifische Projektsammlung, auf die Sie dann mit `DTE.VCProjects` oder `DTE.GetObject("VCProjects")`zugreifen können. Sie können auch `Project.Object`eine erstellen, die für `Project.CodeModel`den Projekttyp eindeutig ist, eine , `ProjectItem`die für `ProjectItem.Object`ihr am `ProjectItem.FileCodeModel`häufigsten abgeleitetes Objekt abgefragt werden kann, eine , die verfügbar ist, und eine .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>So tragen Sie ein VSPackage-spezifisches Objekt für ein Projekt bei

1. Fügen Sie die entsprechenden Schlüssel zur *.pkgdef-Datei* Ihres VSPackage hinzu.

     Hier sind beispielsweise die *.pkgdef-Einstellungen* für das C++-Sprachprojekt:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementieren Sie den <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Code in der Methode, wie im folgenden Beispiel.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     Im Code `g_wszAutomationProjects` ist der Name Ihrer Projektsammlung. Die `GetAutomationProjects` Methode erstellt ein Objekt, das `Projects` `IDispatch` die Schnittstelle implementiert und einen Zeiger auf das aufrufende Objekt zurückgibt, wie im folgenden Codebeispiel gezeigt.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     Wählen Sie einen eindeutigen Namen für Ihr Automatisierungsobjekt aus. Namenskonflikte sind unvorhersehbar, und Kollisionen bewirken, dass ein in Konflikt stehender Objektname willkürlich verworfen wird, wenn mehrere Projekttypen denselben Namen verwenden. Sie sollten Ihren Firmennamen oder einen eindeutigen Aspekt des Produktnamens in den Namen des Automatisierungsobjekts aufnehmen.

     Das `Projects` benutzerdefinierte Auflistungsobjekt ist ein bequemer Einstiegspunkt für den verbleibenden Teil des Projektautomatisierungsmodells. Auf Ihr Projektobjekt kann <xref:EnvDTE.Solution> auch über die Projektsammlung zugegriffen werden. Nachdem Sie den entsprechenden Code und die `Projects` entsprechenden Registrierungseinträge erstellt haben, die Denverbrauchern Auflistungsobjekte bereitstellen, muss die Implementierung die verbleibenden Standardobjekte für das Projektmodell bereitstellen. Weitere Informationen finden Sie unter [Projektmodellierung](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
