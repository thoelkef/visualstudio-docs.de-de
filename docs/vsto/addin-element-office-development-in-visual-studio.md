---
title: '&lt;Add-in&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb2161cbc6633163ba8fba3f8eb678cb0ad72333
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304466"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;Add-in&gt; -Element (Office-Entwicklung in Visual Studio)
  Die **-Add-in** Element der `vstav3` -Namespace enthält spezifische Informationen zu Microsoft Office VSTO-Add-ins und Anpassungen auf Dokumentebene, die mit Visual Studio entwickelt wurden.  

## <a name="syntax"></a>Syntax  

```xml
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  

## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die **-Add-in** Element der `vstav3` -Namespace enthält Informationen zu Office-Projektmappe, und Microsoft Office-Anwendung. Dieses Element muss sich im folgenden Namespace befinden: `vstav3=urn:schemas-microsoft-com:vsta.v3`. Untergeordnete Elemente müssen sich ebenfalls in diesem Namespace befinden.  

 Das `addin` -Element weist keine Attribute auf.  

 Das `addin` -Element weist die folgenden untergeordneten Elemente auf:  

### <a name="entrypoints"></a>entryPoints  
 Erforderlich. Die **EntryPoints** Element finden Sie im [ &#60;EntryPoints&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  

### <a name="update"></a>aktualisieren  
 Erforderlich. Die **aktualisieren** Element finden Sie im [ &#60;aktualisieren&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md).  

### <a name="postactions"></a>postActions  
 Dies ist optional. Die **PostActions** Element finden Sie im [ &#60;PostActions&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).  

### <a name="application"></a>Anwendung  
 Erforderlich. Die **Anwendung** Element finden Sie im [ &#60;Anwendung&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md).  

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene  

### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht die **-Add-in** Element in einer Anwendungsebene Office-Projektmappe, die mithilfe von [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  

### <a name="code"></a>Code  

```xml
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.ThisWorkbook">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet1">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet2">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet3">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:document   
          solutionId="73e" />  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in  

### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht die **-Add-in** Element in einer Anwendungsebene Office-Projektmappe, die mithilfe von [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  

### <a name="code"></a>Code  

```xml
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoOutlookAddIn.ThisAddIn">  
        <assemblyIdentity   
          name="ContosoOutlookAddIn"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:appAddIn   
          application="Outlook"   
          loadBehavior="3"   
          keyName="ContosoOutlookAddIn">  
          <vstov4:friendlyName>  
            ContosoOutlookAddIn  
          </vstov4:friendlyName>  
          <vstov4:description>  
            ContosoOutlookAddIn - Outlook VSTO Add-in   
            created with Visual Studio Tools for Office  
          </vstov4:description>  
          <vstov4:formRegions>  
            <vstov4:formRegion  
                name="OutlookAddIn1.FormRegion1">  
              <vstov4:messageClass name="IPM.Note" />  
              <vstov4:messageClass name="IPM.Contact" />  
              <vstov4:messageClass name="IPM.Appointment" />  
            </vstov4:formRegion>  
          </vstov4:formRegions>  
        </vstov4:appAddIn>  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  

## <a name="see-also"></a>Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
