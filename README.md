1. The project implements table with information about people using Mate academy server API.
After first loading you'll see a table with information received from the server. But it is not just
a table with data from server. There are some handlers which show you calculated information and
some features for user interaction with the given table. React router is used in the application,
so many components, features and variables are connected with url.
- Home page appears at `/` with just a title `Home page`;
- People page appears at `/people` with a title `Peope page` and table;
- User is redirected to `/` from `/home`;
- NotFoundPage with a title `Page not found` is shown for all unsuitable URLs;
- A Header component is visible everywhere with navigation links to both pages;
- getPeople method fetchs people from Mate API when PeoplePage is opened. Information about mother and father
which are found by motherName and fatherName properties is added to the person object for future use. Female persons'
names in the table are written by red color and male – by blue color. There are three ways of infomation about parents
displaying:
  `information is absent` text, when the person object's corresponding parent property is null,
  parent name with black color and additional text `(Detailed info is absent)`, if there is a name in the person object
  corresponding property but there is no information about such person on the server,
  parent name and years of living if there is an information on server about the parent.
- PeopleTable component accepts an array of people as a param and renders them in a table with columns: 
name, sex, born, died, mother, father.
- Each name is a link to a person (it uses slug property from the person object). Click on each name adds the
appropriate slug to the url and row with the selected person becomes highlighted (if you click on father or mother
the app will highlight mother or father in the table, if exists, not that row which you clicked). If you copy the url
and insert it into browser's adress bar and url contains slug, the appropriate person will be highlighted in the table.
- Table can be sorted by columns (except mother and father columns), also you can find a person using search field
(the search uses fields name, motherName, fatherName). The query from the search input and sorting params are displaying
in the url. Also if you paste some url with search params they will be applied to the table if valid. The column by which
sorting is applied is highlited by the * and icon with sort direction is displaied.
Search query in the url is not updated immediately. There should be a pause of 500ms in typing to display changes.
- There is a NewPerson component which represents a form to add new people. It appeares above the table on 'Add new person'
button click (button dissapeares at the moment). Sex may be chosen among 2 options with
radio buttons. Mother and father are selects with with all the women and men from the table (and server) accordingly. When the
person is added you'll be navigated back to the `/people` page. There is a data validation and restrictions in the form:
    - name should contain only letters and spaces
    - born and died are valid years between 1400 and the current year
    - died is disabled if born is empty
    - died - born should be >= 0 and < 150
    - mother and father fields are optional
    - the list of mothers and fathers is updating according to the entered born year (they must be alive)
    (selects are empty and disabled before the born year was entered).

2. Technologies stack: HTML5, CSS3, SASS (I've used markup and CSS from another task and added some new), JS, TS, React.

3. Preview link: https:/mykhailoivchenko.github.io/react-people-table/

4. When you add a new person, be noted, that changes in table will be available only until the page reloading.
The new person data is saved just in array, the application doesn't send it to server or local storage. So new persons
exist only till the next persons' data fetching from server.
