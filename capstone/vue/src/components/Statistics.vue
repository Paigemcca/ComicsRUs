<template>
    <div id="statistics-table">
        <h1>Top 5 Comic Collector Leaderboard</h1>
        <table>
        <tr>
            <th>User Name</th>
            <th>Total Number of Comics</th>
        </tr>
        <tr >
            <td>comicFan9000</td>
            <td>734</td>
        </tr>
        </table>
        <table>
        <tr>
            <th>User Name</th>
            <th>Total Number of Comics</th>
        </tr>
        <tr >
            <td>super()hero</td>
            <td>455</td>
        </tr>
        </table>
        <table>
        <tr>
            <th>User Name</th>
            <th>Total Number of Comics</th>
        </tr>
        <tr >
            <td>marvelLover84</td>
            <td>399</td>
        </tr>
        </table>
        <table>
        <tr>
            <th>User Name</th>
            <th>Total Number of Comics</th>
        </tr>
        <tr >
            <td>MarvelManiac</td>
            <td>378</td>
        </tr>
        </table>
        <table>
        <tr>
            <th>User Name</th>
            <th>Total Number of Comics</th>
        </tr>
        <tr >
            <td>Captain Marvel</td>
            <td>274</td>
        </tr>
        </table>
    </div>
  
</template>

<script>
import userService from '../services/UserService.js'
export default {
    data() { 
        return {
            length: 0,
            allComics:[],
            allUsers:[],
            user_id: this.user_id,
            user: {
                userId: 0,
                username: "",
                password_hash: "",
                role: ""
            },
            currentSort: 'comicAmount',
            currentSortDir: 'asc'
        }
    },
    methods: {
        sort:function(s) {
            if(s === this.currentSort) {
                this.currentSortDir = this.currentSortDir==='asc'?'desc':'asc';
            }
            this.currentSort = s;
        }
    },
    created(){
        userService.getAllUsers().then(response =>{ 
            this.allUsers = response.data;
        });
    },
    computed: {
        sortedComics:function() {
            return this.users.slice().sort((a,b) => {
            let modifier = 1;
            if(this.currentSortDir === 'desc') modifier = -1;
            if(a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
            if(a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
            return 0;
        });
    }
    }
}
</script>

<style>
#statistics-table {
    padding-top: 200px;
}
tr {
    margin-left:400px;
}

</style>