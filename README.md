<!DOCTYPE html>
<html ng-app="libraryManagement">
<head>
  <title>Library Management</title>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      background-color: #f4f4f4;
      color: #333;
    }

    h1 {
      text-align: center;
      color: #4CAF50;
    }

    table {
      width: 80%;
      margin: 20px auto;
      border-collapse: collapse;
      background: #fff;
      border: 1px solid #ccc;
    }

    th, td {
      padding: 10px;
      border: 1px solid #ccc;
      text-align: left;
    }

    th {
      background-color: #4CAF50;
      color: white;
    }

    form {
      text-align: center;
      margin-top: 20px;
    }

    form input, form button {
      padding: 10px;
      margin: 5px;
    }

    form button {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }

    form button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body ng-controller="libraryController">
  <h1>Library App</h1>
  <table>
    <tr>
      <th>Category</th>
      <th>Count</th>
    </tr>
    <tr ng-repeat="book in library">
      <td>{{ book.category }}</td>
      <td><input type="number" ng-model="book.count" /></td>
    </tr>
  </table>
  <form ng-submit="addCategory()">
    <input type="text" ng-model="newCategory" placeholder="Category Name" />
    <input type="number" ng-model="newCount" placeholder="Count" />
    <button type="submit">Add Category</button>
  </form>
  <script>
    angular.module('libraryManagement', [])
      .controller('libraryController', ['$scope', function($scope) {
        $scope.library = [
          { category: 'Fiction', count: 120 },
          { category: 'Non-Fiction', count: 80 },
          { category: 'Science', count: 150 },
          { category: 'Mathematics', count: 70 }
        ];

        $scope.addCategory = function() {
          if ($scope.newCategory && $scope.newCount) {
            $scope.library.push({ category: $scope.newCategory, count: $scope.newCount });
            $scope.newCategory = '';
            $scope.newCount = '';
          }
        };
      }]);
  </script>
</body>
</html>