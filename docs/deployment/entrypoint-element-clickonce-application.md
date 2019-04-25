---
title: '&lt;EntryPoint&gt; -Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 615a606dc4d04682a9d5a1a69c91b4d2cd67de15
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665258"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;EntryPoint&gt; -Element (ClickOnce-Anwendung)
Identifiziert die Assembly, die sollten ausgeführt, wenn dies [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf einem Clientcomputer ausgeführt wird.

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `entryPoint` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2` -Namespace. Gibt es möglicherweise nur eine `entryPoint` Elements, das in einem Anwendungsmanifest definiert.

 Das `entryPoint` -Element hat das folgende Attribut.

|Attribut|Beschreibung|
|---------------|-----------------|
|`name`|Dies ist optional. Dieser Wert wird nicht von .NET Framework verwendet.|

 `entryPoint` hat die folgenden Elemente:

## <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Die Rolle des `assemblyIdentity` und ihre Attribute in [ \<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-application.md).

 Die `processorArchitecture` Attribut dieses Elements und dem `processorArchitecture` im definierten Attribut der `assemblyIdentity` an anderer Stelle in der Anwendung Manifest muss übereinstimmen.

## <a name="commandline"></a>commandLine
 Erforderlich. Muss ein untergeordnetes Element des der `entryPoint` Element. Es hat keine untergeordneten Elemente und weist folgende Attribute.

| Attribut | Beschreibung |
|--------------| - |
| `file` | Erforderlich. Einen lokalen Verweis auf die Startassembly für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieser Wert kann nicht einen Schrägstrich (/) oder umgekehrten Schrägstrich enthalten (\\) Pfadtrennzeichen. |
| `parameters` | Erforderlich. Beschreibt die Aktion an, mit dem Einstiegspunkt an. Der einzige gültige Wert ist `run`; Wenn eine leere Zeichenfolge angegeben wird, `run` wird angenommen. |

## <a name="customhostrequired"></a>customHostRequired
 Dies ist optional. Wenn enthalten, gibt an, dass diese Bereitstellung eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt werden, und ist keine eigenständige Anwendung.

 Wenn dieses Element vorhanden ist, ist die `assemblyIdentity` und `commandLine` Elemente dürfen nicht auch vorhanden sein. Wenn dies der Fall, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] löst einen Validierungsfehler während der Installation.

 Dieses Element weist keine Attribute und keine untergeordneten Elemente.

## <a name="customux"></a>customUX
 Dies ist optional. Gibt an, dass die Anwendung installiert ist und durch ein individuelles Installationsprogramm erstellt, verwaltet und nicht Eintrag im Menü Start, Kontextmenü oder hinzufügen erstellen oder Entfernen der Eintrag "Programme".

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Eine Anwendung mit dem CustomUX Element muss einem individuelles Installationsprogramm erstellt, die verwendet bieten die <xref:System.Deployment.Application.InPlaceHostingManager> -Klasse, Vorgänge zu installieren. Eine Anwendung mit diesem Element kann nicht durch Doppelklicken auf die erforderliche Manifest oder eine setup.exe-Bootstrapper installiert werden. Das benutzerdefinierte Installationsprogramm kann Start Menüeinträge, Verknüpfungen und Software -Einträge erstellen. Wenn das benutzerdefinierte Installationsprogramm kein Eintrag in "Software" erstellt wird, müssen sie die Abonnement-ID, die von bereitgestellte speichern die <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> -Eigenschaft und der Benutzer später deinstallieren die Anwendung durch Aufrufen der <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> Methode. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Hinweise
 Dieses Element identifiziert die Assembly und den Einstiegspunkt für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

 Sie können keine `commandLine` zum Übergeben von Parametern in Ihrer Anwendung zur Laufzeit. Sie können auf zugreifen, Abfragezeichenfolgen-Parameter für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung aus der Anwendung <xref:System.AppDomain>. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht eine `entryPoint` Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) Thema.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
