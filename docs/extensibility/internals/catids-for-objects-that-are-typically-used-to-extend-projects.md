---
title: "CATIDs f&#252;r Objekte, die in der Regel verwendet werden, um Projekte zu erweitern. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages CATIDs"
  - "GUIDs, die VSPackages"
  - "CATIDs für VSPackages"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# CATIDs f&#252;r Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der folgenden Tabelle werden die CATID auf, die verwendet werden, um `Project` und `ProjectItem` Automatisierungsobjekte für [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]und [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte zu erweitern.  Dieses CATID wird in VSLangProj.olb definiert.  
  
## Listen der CATID  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614\-D0D5\-11D2\-8599\-006097 C68 E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615\-D0D5\-11D2\-8599\-006097 C68 E81}|  
  
## Visual Basic CATID  
 In der folgenden Tabelle werden die CATID auf, die verwendet werden, um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Suchobjekte zu erweitern.  Alle sie werden in VSLangProj.olb definiert.  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FD C879 \- C32 A\-4751\-A3D3\-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11\-14EB\-489b\-87F0\-F01 C52 AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D\-3 C72 \-40A5\-95A0\-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932D C619 \-2EAA\-4192\-B7E6\-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812\-8191\-4e81\-B7B3\-174045AB0 CB5}|  
  
## Visual C\# CATID  
 Im folgenden CATID kann verwendet werden, um [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Suchobjekte zu erweitern.  Alle sie werden in VSLangProj.olb definiert.  
  
|Name|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003\-DE95\-4d60\-96B0\-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12 CE10 A\-227F\-4963\-ADB6\-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF\-ED4E\-48B0\-8 C7 b C74 EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|CC84 914FE278\-054A\-45DB\-BF9E\-5F22484 {C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8\- C855 \-4a4e\-95A5\- CB45 C67 D6 C27}|  
  
## C\+\+ CATID  
 Im Folgenden [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projektsystem CATID werden nicht in Typbibliotheken in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 verfügbar gemacht und müssen im Code angegeben werden, wenn Sie diese Projektobjekte erweitern möchten.  Dieses CATID wird in Typbibliotheken in späteren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]enthalten.  
  
|Name|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
  
 Im folgenden Codebeispiel wird das Programmieren dieses CATID im Code.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Im Folgenden [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projektsystem CATID werden ebenfalls nicht in Typbibliotheken in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 verfügbar gemacht und müssen im Code angegeben werden, wenn Sie diese Projektobjekte erweitern möchten.  Dieses CATID ist nur in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 nicht zur Verfügung und wird in späteren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügbar sein.  
  
|Name|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE\-20A7\-48e4\-A CA1 \-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3\- C60 A\-44f4\-A74B\-14 C90 EF9CACE}|  
|`CVCReferences`|{FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683}|  
  
 Das folgende Codebeispiel veranschaulicht das Programmieren dieses CATID im Code:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Die GUID für die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen werden in der folgenden Tabelle dargestellt.  
  
|Projekttyp|GUID|  
|----------------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04E C0 \-301F\-11D3\-BF4B\-00 C04 F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F}|  
  
## Siehe auch  
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)