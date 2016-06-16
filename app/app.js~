(function(){
    'use strict';

    angular.module('main', ['ngRoute', 'ngTable'])
        .config(['$routeProvider',
            function ($routeProvider) {
                $routeProvider.
                    when('/', {
                        templateUrl: 'views/intro/overview.html',
                        controller: 'introController',
                        controllerAs: 'vm'
                    });
            }])
        .controller('introController', function(Auth,NgTableParams){
            var self = this;
		Auth.getData()
		    .success(function (post) {
			var data =post;
			self.tableParams = new NgTableParams({ count: 5}, { counts: [5, 10, 25], dataset: data});
		    })
		    .error(function (error) {
		       $scope.errorMsg = 'Something went Wrong!! Please try again';
		    });
        })
	.factory('Auth',['$http',function ($http){
	    var user;
	    var serviceBase = 'service/'
	    var obj = {};

	    obj.getData = function(){
		return $http({
		    method: 'GET',
		    url: serviceBase + 'posts.json',
		    headers: {'Content-Type': 'application/x-www-form-urlencoded'}
		 });
	    };

	    return obj;
	}]);
})();
