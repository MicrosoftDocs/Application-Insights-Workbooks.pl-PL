# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a><span data-ttu-id="7f203-101">Wybieranie zestawu zasobów do analizowania w skoroszytach</span><span class="sxs-lookup"><span data-stu-id="7f203-101">Picking a set of resources to analyze in workbooks</span></span>

<span data-ttu-id="7f203-102">Szablon `Resource Picker` ułatwia rozpoczęcie pracy z parametrami subskrypcji, grupy zasobów i zasobów w celu skonfigurowania kontekstu wejściowego skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="7f203-102">The `Resource Picker` template gets you started with subscription, resource group and resource parameters to set up the input context of your workbook.</span></span> <span data-ttu-id="7f203-103">Domyślne parametry są ustawione do wybierania maszyn wirtualnych, ale można je skonfigurować do wybierania dowolnego typu zasobu.</span><span class="sxs-lookup"><span data-stu-id="7f203-103">The default parameters are set to pick virtual machines, but you can configure it to pick any type of resource.</span></span> <span data-ttu-id="7f203-104">Szablon zawiera również kontrolkę zapytania argumentu, która pokazuje, jak używać parametrów w analizach.</span><span class="sxs-lookup"><span data-stu-id="7f203-104">The template also has a ARG query control that shows you how to use the parameters in your analyses.</span></span>

![Image (Obraz)](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a><span data-ttu-id="7f203-106">Konfigurowanie typu zasobu do wybrania</span><span class="sxs-lookup"><span data-stu-id="7f203-106">Setting up the resource type to pick</span></span>

1. <span data-ttu-id="7f203-107">Wybierz pozycję `Edit` na pasku narzędzi skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="7f203-107">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="7f203-108">Teraz powinna być widoczna lista rozwijana `Resource type` przed elementem `Subscriptions`:</span><span class="sxs-lookup"><span data-stu-id="7f203-108">You will now be able to see a drop down `Resource type` before `Subscriptions`:</span></span>

    ![Image (Obraz)](Parameter.png)
3. <span data-ttu-id="7f203-110">Rozwiń listę rozwijaną i wybierz typy zasobów, które mają być wybierane.</span><span class="sxs-lookup"><span data-stu-id="7f203-110">Expand the drop down and select the resource types you want picked.</span></span> <span data-ttu-id="7f203-111">Spowoduje to zaktualizowanie subskrypcji, grupy zasobów i listy rozwijanej zasobów w celu dopasowania do dokonanego wyboru.</span><span class="sxs-lookup"><span data-stu-id="7f203-111">This will update the subscription, resource group and resources drop down to match your selection.</span></span>
4. <span data-ttu-id="7f203-112">Kliknij przycisk `Edit` w prawym dolnym rogu kontrolki parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f203-112">Click the `Edit` button at the bottom right of the parameter control.</span></span>
5. <span data-ttu-id="7f203-113">W siatce parametrów dla wiersza `Resources` zmień kolumnę `Display name` z _Maszyny wirtualne_ na przyjazną nazwę wybranego typu zasobu (np. _Konta magazynu_)</span><span class="sxs-lookup"><span data-stu-id="7f203-113">In the parameters grid, for the row `Resources`, change the `Display name` column from _Virtual machines_ to friendly name of your selected resource type (e.g. _Storage Accounts_)</span></span>
6. <span data-ttu-id="7f203-114">Kliknij pozycję `Done Editing` na pasku narzędzi skoroszytów.</span><span class="sxs-lookup"><span data-stu-id="7f203-114">Click `Done Editing` in the workbooks toolbar.</span></span>

## <a name="selecting-more-or-less-than-10-resources-by-default"></a><span data-ttu-id="7f203-115">Domyślne wybieranie więcej lub mniej niż 10 zasobów</span><span class="sxs-lookup"><span data-stu-id="7f203-115">Selecting more or less than 10 resources by default</span></span>

1. <span data-ttu-id="7f203-116">Wybierz pozycję `Edit` na pasku narzędzi skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="7f203-116">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="7f203-117">Kliknij przycisk `Edit` w prawym dolnym rogu kontrolki parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f203-117">Click the `Edit` button at the bottom right of the parameter control.</span></span>
3. <span data-ttu-id="7f203-118">W siatce parametrów wybierz wiersz `Resources`</span><span class="sxs-lookup"><span data-stu-id="7f203-118">In the parameters grid, select the row for `Resources`</span></span>
4. <span data-ttu-id="7f203-119">Kliknij pasek narzędzi kontrolki ikony `Edit` (lub ołówka).</span><span class="sxs-lookup"><span data-stu-id="7f203-119">Click on the `Edit` (or pencil) icon control toolbar.</span></span>
5. <span data-ttu-id="7f203-120">W okienku `Edit Parameter`, które zostanie wyświetlone, przewiń w dół do edytora `Azure Resource Graph Query`.</span><span class="sxs-lookup"><span data-stu-id="7f203-120">In the `Edit Parameter` pane that pops up, scroll down to the `Azure Resource Graph Query` editor.</span></span> <span data-ttu-id="7f203-121">Powinien on zawierać zapytanie, które wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="7f203-121">It should have a query that looks like this:</span></span>
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    <span data-ttu-id="7f203-122">Kod wybierania zasobów znajduje się w ostatnim wierszu zapytania: `selected = Rank <= 10`.</span><span class="sxs-lookup"><span data-stu-id="7f203-122">The code for resource selection is in the last line of the query: `selected = Rank <= 10`.</span></span> 

6. <span data-ttu-id="7f203-123">Zmień wartość z 10 na inną, aby zmienić domyślny wybór</span><span class="sxs-lookup"><span data-stu-id="7f203-123">Change the value from 10 to a different one to change the default selection</span></span>