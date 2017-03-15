---
title: "Demobeispiel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalyse, Beispiele"
  - "Demobeispiel [Visual Studio-ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Demobeispiel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In den folgenden Verfahren wird das Erstellen des Beispiels für [Exemplarische Vorgehensweise: Analysieren von C\/C\+\+\-Code auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md) veranschaulicht.  Folgende Elemente werden in den Verfahren erstellt:  
  
-   Eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe mit dem Namen CppDemo.  
  
-   Ein statisches Bibliotheksprojekt mit dem Namen CodeDefects.  
  
-   Ein statisches Bibliotheksprojekt mit dem Namen Annotations.  
  
 Darüber hinaus wird in den Verfahren der Code für die Header\- und CPP\-Dateien für die statischen Bibliotheken bereitgestellt.  
  
### Erstellen der CppDemo\-Projektmappe und des CodeDefects\-Projekts  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Neues Projekt**.  
  
2.  Erweitern Sie in der Strukturliste **Projekttypen** den Knoten **Andere Sprachen**, wenn Visual C\+\+ nicht als Standardsprache in VS verwendet wird.  
  
3.  Erweitern Sie **Visual C\+\+**, und klicken Sie dann auf **Allgemein**.  
  
4.  Klicken Sie unter **Vorlagen** auf **Leeres Projekt**.  
  
5.  Geben Sie im Textfeld **Name** die Zeichenfolge **CodeDefects** ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen**.  
  
7.  Geben Sie **CppDemo** im Textfeld **Projektmappenname** ein.  
  
### Konfigurieren des CodeDefects\-Projekts als statische Bibliothek  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf **CodeDefects**, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Erweitern Sie die **Konfigurationseigenschaften**, und klicken Sie dann **Allgemein**.  
  
3.  Wählen Sie in der Liste **Allgemein** den Text in der Spalte neben **Zielerweiterung** aus, und geben Sie **.lib** ein.  
  
4.  Klicken Sie unter **Projektstandards** auf die Spalte neben **Konfigurationstyp** und anschließend auf **Statische Bibliothek \(.lib\)**.  
  
### Hinzufügen der Headerdatei und der Quelldatei zum CodeDefects\-Projekt  
  
1.  Erweitern Sie im Projektmappen\-Explorer **CodeDefects**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
2.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **Headerdatei \(.h\)**.  
  
3.  Geben Sie in das Feld **Name** den Namen **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code, und fügen Sie ihn im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Editor in die Datei **Bug.cpp** ein.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.  
  
6.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C\+\+\-Datei \(.cpp\)**.  
  
7.  Geben Sie in das Feld **Name** den Namen **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code und fügen sie ihn in die Datei "Bug.h" im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Editor ein.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
### Hinzufügen und Konfigurieren des Annotations\-Projekts als statische Bibliothek  
  
1.  Klicken Sie im Projektmappen\-Explorer auf **CppDemo**, zeigen Sie auf **Hinzufügen**, und klicken Sie auf **Neues Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** den Knoten "Visual C\+\+", klicken Sie auf **Allgemein** und anschließend auf **Leeres Projekt**.  
  
3.  Geben Sie im Textfeld **Name** den Namen **Annotations** ein, und klicken Sie auf **Hinzufügen**.  
  
4.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf **Annotations**, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Erweitern Sie die **Konfigurationseigenschaften**, und klicken Sie dann **Allgemein**.  
  
6.  Wählen Sie in der Liste **Allgemein** den Text in der Spalte neben **Zielerweiterung** aus, und geben Sie **.lib** ein.  
  
7.  Klicken Sie unter **Projektstandards** auf die Spalte neben **Konfigurationstyp** und anschließend auf **Statische Bibliothek \(.lib\)**.  
  
### Hinzufügen der Headerdatei und der Quelldatei zum Annotations\-Projekt  
  
1.  Erweitern Sie im Projektmappen\-Explorer den Knoten **Annotations**, und klicken Sie mit der rechten Maustaste auf **Headerdateien**. Klicken Sie auf **Hinzufügen** und dann auf **Neues Element**.  
  
2.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Headerdatei \(.h\)**.  
  
3.  Geben Sie in das Feld **Name** den Namen **annotations.h** ein, und klicken Sie dann auf **Hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code und fügen sie ihn in die Datei **annotations.h** im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Editor ein.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.  
  
6.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **C\+\+\-Datei \(.cpp\)**.  
  
7.  Geben Sie im Feld **Name annotations.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code und fügen sie ihn in die Datei **annotations.cpp** im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Editor ein.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.