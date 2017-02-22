---
title: "Verwenden von Microsoft.VisualStudio.TestTools.UnitTesting-Membern in Komponententests | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# Verwenden von Microsoft.VisualStudio.TestTools.UnitTesting-Membern in Komponententests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Komponententestframework unterstützt Komponententests in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Verwenden Sie beim Schreiben von Komponententests die Klassen und Member im <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>\-Namespace.  Diese Klassen können Sie beim Schreiben eigener Komponententests verwenden und auch zum Bearbeiten von Komponententests, die zuvor aus zu testendem Code generiert wurden.  
  
## Gruppen von Elementen  
 Um Ihnen einen besseren Überblick über das Komponententestframework zu geben, werden in diesem Abschnitt die Elemente des UnitTesting\-Namespace anhand ihrer Funktionen in Gruppen unterteilt.  
  
> [!NOTE]
>  Attributelemente, deren Namen auf die Zeichenfolge Attribute enden, können mit oder ohne diese Zeichenfolge verwendet werden.  Beispielsweise besitzen die folgenden beiden Codebeispiele dieselbe Funktion:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### Elemente für datengesteuerte Tests  
 Verwenden Sie die folgenden Elemente zum Einrichten datengesteuerter Komponententests.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines datengesteuerten Komponententests](../test/how-to-create-a-data-driven-unit-test.md) und [Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## Attribute zur Einrichtung einer Aufrufreihenfolge  
 Ein um eines der folgenden Attribute ergänztes Codeelement wird zu dem von Ihnen angegebenen Zeitpunkt aufgerufen.  Weitere Informationen finden Sie unter [Anatomy of a Unit Test](http://msdn.microsoft.com/de-de/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### Für Assemblys  
 AssemblyInitialize und AssemblyCleanup werden unmittelbar nach dem Laden der Assembly und vor dem Entladen der Assembly aufgerufen.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### Für Klassen  
 ClassInitialize und ClassCleanup werden unmittelbar nach dem Laden der Klasse und vor dem Entladen der Klasse aufgerufen.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### Für Testmethoden  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## Attribute zur Identifikation von Testklassen und Testmethoden  
 Jede Testklasse muss das TestClass\-Attribut, jede Testmethode das TestMethod\-Attribut aufweisen.  Weitere Informationen finden Sie unter [Anatomy of a Unit Test](http://msdn.microsoft.com/de-de/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Assert\-Klassen und zugehörige Ausnahmen  
 Mit Komponententests kann das Verhalten bestimmter Anwendungsfunktionen überprüft werden. Zu diesem Zweck fügen Sie verschiedene Assert\-Anweisungen, Ausnahmen oder Attribute in den Test ein.  Weitere Informationen finden Sie unter [Verwenden der Assert\-Klassen](../test/using-the-assert-classes.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## Die TestContext\-Klasse  
 Die folgenden Attribute und die zugehörigen Werte werden im Eigenschaftenfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für einzelne Testmethoden angezeigt.  Auf diese Attribute sollte nicht im Code für den Komponententest zugegriffen werden.  Stattdessen wirken sie sich auf die Art und Weise aus, in der der Komponententest verwendet oder ausgeführt wird – von Ihnen über die IDE von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder vom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Testmodul. Beispielsweise werden einige dieser Attribute als Spalten im Fenster Test Manager und im Fenster Testergebnisse angezeigt, sodass Sie sie verwenden können, um Tests und Testergebnisse zu gruppieren und zu sortieren.  Zu diesen Attributen zählt TestPropertyAttribute, mit dem einem Komponententest beliebige Metadaten hinzugefügt werden können.  So können Sie damit z. B. den Namen eines Testlaufs speichern, der mit dem betreffenden Test durchgeführt wird, indem Sie den Komponententest mit `[TestProperty("TestPass", "Accessibility")]` kennzeichnen.  Sie können so auch einen Angabe des betreffenden Testtyps speichern: `[TestProperty("TestKind", "Localization")]`.  Die mit diesem Attributs erstellte Eigenschaft und der zugewiesene Eigenschaftswert werden im Eigenschaftenfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter der Überschrift **Testspezifisch** angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## Testkonfigurationsklassen  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## Attribute zum Generieren von Berichten  
 Die Attribute in diesem Abschnitt stellen eine Beziehung zwischen der Testmethode, für die sie angegeben wurden, und Entitäten in der Projekthierarchie eines [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]\-Teamprojekts her.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## Mit privaten Accessoren verwendete Klassen  
 Wie unter [Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/de-de/2056c6a7-6672-42a7-8f53-fead33c56deb) beschrieben, können Sie einen Komponententest für eine private Methode generieren.  Bei dieser Generierung wird eine private Accessorklasse erstellt, die ein Objekt der PrivateObject\-Klasse instanziiert.  Die PrivateObject\-Klasse ist eine Wrapperklasse, die Reflektion als Teil des privaten Accessorprozesses verwendet.  Sie ähnelt der PrivateType\-Klasse, diese wird jedoch nicht zum Aufrufen privater Instanzmethoden, sondern zum Aufrufen privater statischer Methoden verwendet.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>