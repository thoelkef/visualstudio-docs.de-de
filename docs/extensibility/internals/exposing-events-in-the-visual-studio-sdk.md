---
title: "Verf&#252;gbarmachen von Ereignissen in Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ereignisse [Visual Studio], bereitstellen"
  - "Automatisierung [Visual Studio SDK], Ereignisse verfügbar machen"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Verf&#252;gbarmachen von Ereignissen in Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Sie mithilfe der Automatisierung Ereignissen der Datenquelle. Es wird empfohlen, dass die Quelle von Ereignissen für Projekte und Projektelemente.  
  
 Ereignisse werden abgerufen, indem Automation Consumer aus der <xref:EnvDTE.DTEClass.Events%2A> Objekt oder <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Die Umgebung ruft `IDispatch::Invoke` mithilfe der `DISPATCH_METHOD` oder `DISPATCH_PROPERTYGET` Flags an, die ein Ereignis zurück.  
  
 Der folgende Prozess wird erläutert, wie die VSPackage-spezifische Ereignisse zurückgegeben werden.  
  
1.  Die Umgebung wird gestartet.  
  
2.  Er liest aus der Registrierung alle Wertnamen unter die Automatisierung, AutomationEvents und AutomationProperties Schlüssel von allen VSPackages und speichert diese Namen in einer Tabelle.  
  
3.  In diesem Beispiel ruft ein Automation-Consumer `DTE.Events.AutomationProjectsEvents` oder `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  Die Umgebung sucht von der String-Parameter in der Tabelle und die entsprechenden VSPackage lädt.  
  
5.  Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode mit dem Namen im Aufruf; in diesem Beispiel AutomationProjectsEvents oder AutomationProjectItemsEvents zu übergeben.  
  
6.  Das VSPackage erstellt ein Stammobjekt, die Methoden, z. B. enthält `get_AutomationProjectsEvents` und `get_AutomationProjectItemEvents` und gibt dann einen IDispatch-Zeiger auf das Objekt zurück.  
  
7.  Die Umgebung Ruft die entsprechende Methode, die basierend auf den Namen in der Automation-Aufruf übergeben.  
  
8.  Die `get_` Methode erstellt ein anderes IDispatch-basierte-Ereignisobjekt, das sowohl implementiert die `IConnectionPointContainer` Schnittstelle und die `IConnectionPoint` -Schnittstelle und eine IDispatchpointer für das Objekt zurückgegeben.  
  
 Um ein Ereignis verfügbar zu machen, mithilfe der Automatisierung, muss die Reaktion auf einen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> "und" überwachen, für die Zeichenfolgen, die Sie an der Registrierung hinzufügen. Im Beispiel für den Basic-Projekts sind die Zeichenfolgen "BscProjectsEvents" und "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Registrierungseinträge aus dem Beispiel Basic-Projekts  
 Dieser Abschnitt zeigt, wo Automation Ereigniswerte zur Registrierung hinzugefügt.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "Das Objekt AutomationProjectEvents AutomationProjectEvents"="gibt"  
  
 "Das Objekt AutomationProjectItemsEvents AutomationProjectItemEvents"="gibt"  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|Standardwert (@)|REG_SZ|Nicht verwendete|Nicht verwendet. Sie können das Feld "Daten" Dokumentation verwenden.|  
|AutomationProjectsEvents|REG_SZ|Name des Ereignisobjekts.|Nur der Schlüsselname ist relevant. Sie können das Feld "Daten" Dokumentation verwenden.<br /><br /> In diesem Beispiel stammen aus dem grundlegenden projektbeispiel.|  
|AutomationProjectItemEvents|REG_SZ|Name des Ereignisobjekts|Nur der Schlüsselname ist relevant. Sie können das Feld "Daten" Dokumentation verwenden.<br /><br /> In diesem Beispiel stammen aus dem grundlegenden projektbeispiel.|  
  
 Wenn keines der Objekte von einem Consumer Automatisierung angefordert werden, erstellen Sie ein Stammobjekt, die Methoden für jedes Ereignis enthält, die das VSPackage unterstützt. Die Umgebung Ruft die entsprechende `get_` Methode für dieses Objekt. Z. B. wenn `DTE.Events.AutomationProjectsEvents` aufgerufen wird, die `get_AutomationProjectsEvents` Methode für das Stammobjekt aufgerufen wird.  
  
 ![Ereignisse in Visual Studio-Projekt](~/docs/extensibility/internals/media/projectevents.gif "ProjectEvents")  
Automatisierungsmodell für Ereignisse  
  
 Die Klasse `CProjectEventsContainer` stellt das Quellobjekt für BscProjectsEvents, während `CProjectItemsEventsContainer` das Quellobjekt für BscProjectItemsEvents darstellt.  
  
 In den meisten Fällen müssen Sie ein neues Objekt für jede Anforderung Ereignis zurückgeben, da die meisten Ereignisobjekten ein Filterobjekt in Anspruch nehmen. Wenn Sie das Ereignis ausgelöst werden, überprüfen Sie diesen Filter, um sicherzustellen, dass der Ereignishandler aufgerufen wird.  
  
 AutomationEvents.h und AutomationEvents.cpp enthält Deklarationen und Implementierungen von Klassen in der folgenden Tabelle.  
  
|Klasse|Beschreibung|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementiert ein Stamm Ereignisobjekt abgerufen, die aus der `DTE.Events` Objekt.|  
|`CProjectsEventsContainer` und `CProjectItemsEventsContainer`|Implementieren Sie die Ereignis-Objekte, die die entsprechenden Ereignissen ausgelöst werden.|  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie für die Reaktion auf eine Anforderung für ein Ereignisobjekt.  
  
```cpp#  
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
  
 Im obigen Code `g_wszAutomationProjects` ist der Name, der die Projektsammlung ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") und `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") sind die Namen der Projektereignisse und Projektelemente Ereignisse, die von der VSPackage-Implementierung bezogen werden.  
  
 Ereignisobjekte werden abgerufen, an dem zentralen Speicherort, der `DTE.Events` Objekt. Auf diese Weise werden alle Objekte zusammengefasst, damit ein Endbenutzer nicht unbedingt das gesamte Objektmodell zum Suchen eines bestimmten Ereignisses zu durchsuchen. Dies können Sie bereitstellen, die bestimmte VSPackage-Objekte, anstatt Sie Ihren eigenen Code für eine systemweite Ereignisse zu implementieren. Für den Endbenutzer, die muss finden jedoch ein Ereignis für Ihre `ProjectItem` -Schnittstelle, es ist nicht sofort klar, von dem das Ereignisobjekt abgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK-Beispiele](../../misc/vssdk-samples.md)