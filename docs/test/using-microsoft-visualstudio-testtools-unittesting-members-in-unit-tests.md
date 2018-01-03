---
title: Verwenden von Microsoft.VisualStudio.TestTools.UnitTesting-Membern in Komponententests | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: "6"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 9468b796a601956941fb8d913e6ae6198afbfa59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Verwenden von Microsoft.VisualStudio.TestTools.UnitTesting-Membern in Komponententests
Das Framework für Komponententests unterstützt Komponententests in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Verwenden Sie zum Programmieren von Komponententests die Klassen und Member im Namespace <Microsoft.VisualStudio.TestPlatform.UnitTestFramework>. Diese können Sie verwenden, wenn Sie den Komponententest von Grund auf neu geschrieben haben oder einen Komponententest optimieren, der aus dem getesteten Code generiert wurde.  
  
## <a name="groups-of-elements"></a>Elementegruppen  
 Für einen besseren Überblick über das Framework für Komponententests werden die Elemente des Namespace UnitTesting in diesem Abschnitt in Gruppen verwandter Funktionen aufgeführt.  
  
> [!NOTE]
>  Attributelemente, deren Namen mit der Zeichenfolge „Attribute“ enden, können mit oder ohne die Zeichenfolge „Attribute“ verwendet werden. So wird beispielsweise mit den folgenden beiden Codebeispiele das gleiche Ergebnis erzielt:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Für datengesteuerte Tests verwendete Elemente  
 Verwenden Sie die folgenden Elemente zum Einrichten eines datengesteuerten Komponententests. Weitere Informationen finden Sie unter [How To: Create a Data-Driven Unit Test (Vorgehensweise: Erstellen eines datengesteuerten Komponententests)](../test/how-to-create-a-data-driven-unit-test.md) und [Walkthrough: Using a Configuration File to Define a Data Source (Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle)](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Zum Einrichten einer Aufrufreihenfolge verwendete Attribute  
 Ein mit einem der folgenden Attribute versehenes Codeelement wird zum angegebenen Zeitpunkt aufgerufen. Weitere Informationen finden Sie unter [Anatomy of a Unit Test (Aufbau eines Komponententests)](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### <a name="for-assemblies"></a>Für Assemblys  
 AssemblyInitialize und AssemblyCleanup werden direkt nach dem Laden und direkt vor dem Entladen der Assembly aufgerufen.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Für Klassen  
 ClassInitialize und ClassCleanup werden direkt nach dem Laden und direkt vor dem Entladen der Klasse aufgerufen.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Für Testmethoden  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Zum Angeben von Testklassen und Testmethoden verwendete Attribute  
 Jede Testklasse muss das TestClass-Attribut aufweisen und jede Testmethode das TestMethod-Attribut. Weitere Informationen finden Sie unter [Anatomy of a Unit Test (Aufbau eines Komponententests)](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Assert-Klassen und zugehörige Ausnahmen  
 Im Rahmen von Komponententests kann mit verschiedenen Arten von Assert-Anweisungen, -Ausnahmen und -Attributen überprüft werden, ob sich eine Anwendung auf eine bestimmte Weise verhält. Weitere Informationen finden Sie unter [Verwenden der Assert-Klassen](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>Die TestContext-Klasse  
 Die folgenden Attribute und die diesen zugewiesenen Werte werden im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Eigenschaftenfenster für eine bestimmte Testmethode angezeigt. Diese Attribute dienen nicht dem Zugriff über den Code des Komponententests. Vielmehr beeinflussen sie, entweder durch Sie über die IDE von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder über das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Testmodul, wie der Komponententest verwendet bzw. ausgeführt wird. Einige dieser Attribute werden beispielsweise im Fenster „Test Manager“ und im Fenster „Testergebnisse“ in Spalten angezeigt. Das bedeutet, dass Sie sie zum Gruppieren und Sortieren von Tests und Testergebnissen verwenden können. TestPropertyAttribute ist ein Attribut dieser Art. Mit ihm können beliebige Metadaten zu Komponententests hinzugefügt werden. Sie können es beispielsweise verwenden, um den Namen eines Testdurchlauf zu speichern, der von diesem Test abgedeckt wird, indem Sie den Komponententest mit `[TestProperty("TestPass", "Accessibility")]` kennzeichnen. Oder Sie können es verwenden, um einen Indikator zu speichern, der die Art des Test angibt: `[TestProperty("TestKind", "Localization")]`. Die Eigenschaft, die durch die Verwendung dieses Attributs erstellt wird, und der zugewiesene Eigenschaftswert werden im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Eigenschaftenfenster unter der Überschrift **Testspezifisch** angezeigt.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Testkonfigurationsklassen  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Zum Generieren von Berichten verwendete Attribute  
 Die in diesem Abschnitt beschriebenen Attribute verknüpfen die Testmethode, in der sie enthalten sind, mit Entitäten in der Projekthierarchie eines [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]-Teamprojekts.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Mit privaten Accessoren verwendete Klassen  
 Wie unter [Using Publicize to Create a Private Accessor (Verwenden von Publicize zum Erstellen eines privaten Accessors)](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb) beschrieben, kann ein Komponententest für eine private Methode erstellt werden. Dabei wird eine private Accessor-Klasse erstellt, die ein Objekt der PrivateObject-Klasse instanziiert. Bei der PrivateObject-Klasse handelt es sich um eine Wrapperklasse, die im Rahmen des Prozesses für den privaten Accessor Reflektionen verwendet. Die PrivateType-Klasse ist ähnlich, unterscheidet sich jedoch insofern, als sie zum Aufrufen von privaten statischen Methoden statt von privaten Instanzmethoden verwendet wird.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType  
  
## <a name="see-also"></a>Siehe auch  
 Microsoft.VisualStudio.TestPlatform.UnitTestFramework
