
<!DOCTYPE html>
<html>
<head>
  <title>Table Example</title>
 <script>
  var sortingOrder = true;

  function sortTable(columnIndex) {
    var table, rows, switching, i, x, y, shouldSwitch;
    table = document.getElementById("myTable");
    switching = true;
    while (switching) {
      switching = false;
      rows = table.rows;
      for (i = 1; i < (rows.length - 1); i++) {
        shouldSwitch = false;
        x = rows[i].getElementsByTagName("td")[columnIndex];
        y = rows[i + 1].getElementsByTagName("td")[columnIndex];
        if (sortingOrder) {
          if (x.innerHTML.toLowerCase() > y.innerHTML.toLowerCase()) {
            shouldSwitch = true;
            break;
          }
        } else {
          if (x.innerHTML.toLowerCase() < y.innerHTML.toLowerCase()) {
            shouldSwitch = true;
            break;
          }
        }
      }
      if (shouldSwitch) {
        rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
        switching = true;
      }
    }
    sortingOrder = !sortingOrder;
  }
</script>

  <style>
    table {
      border-collapse: collapse;
      width: 100%;
    }
    th, td {
      text-align: left;
      padding: 8px;
      border: 1px solid #ddd;
    }
    th {
      background-color: #f2f2f2;
    }
    tr:nth-child(even) {
      background-color: #fff;
    }
  </style>
</head>
<body>

  <h1>MollyList.com</h1>

  <table id="myTable">
    <thead>
      <tr>
        <th onclick="sortTable(0)">Name</th>
        <th onclick="sortTable(1)">Stars</th>
        <th onclick="sortTable(2)">Review</th>
        <th onclick="sortTable(3)">Type</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Hawkers</td>
        <td>4.5</td>
        <td>Great product, highly recommend.</td>
        <td>Asian</td>
      </tr>
      <tr>
        <td>Domu</td>
        <td>3.2</td>
        <td>Decent product, but could be better. :)</td>
        <td>Italian</td>
      </tr>
      <tr>
        <td>McDonalds</td>
        <td>5.0</td>
        <td>Amazing product, exceeded my expectations.</td>
        <td>Italian</td>
      </tr>
      <tr>
        <td>Ramen</td>
        <td>2.7</td>
        <td>Poor product, would not recommend.</td>
        <td>Asian</td>
      </tr>
    </tbody>
  </table>

</body>
</html>
