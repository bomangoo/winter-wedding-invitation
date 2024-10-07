<div class="calendar-area">
    <h2>일월의 열여덟번째 날</h2>
    <table>
        <thead>
            <tr>
                <th class="sunday">Sun</th>
                <th>Mon</th>
                <th>Tue</th>
                <th>Wed</th>
                <th>Thu</th>
                <th>Fri</th>
                <th class="saturday">Sat</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td></td>
                <td></td>
                <td></td>
                <td>1</td>
                <td>2</td>
                <td>3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>5</td>
                <td>6</td>
                <td>7</td>
                <td>8</td>
                <td>9</td>
                <td>10</td>
                <td>11</td>
            </tr>
            <tr>
                <td>12</td>
                <td>13</td>
                <td>14</td>
                <td>15</td>
                <td>16</td>
                <td>17</td>
                <td class="dday"><span>18</span></td>
            </tr>
            <tr>
                <td>19</td>
                <td>20</td>
                <td>21</td>
                <td>22</td>
                <td>23</td>
                <td>24</td>
                <td>25</td>
            </tr>
            <tr>
                <td>26</td>
                <td>27</td>
                <td>28</td>
                <td>29</td>
                <td>30</td>
                <td>31</td>
                <td></td>
            </tr>
        </tbody>
    </table>
</div>

<style>
    .calendar-area {
        padding: 4rem 1.5rem;
    }
    .calendar-area h2 {
        padding-bottom: 0.8rem;
        font-size: 1.3rem;
        color: #555;
    }
    table {
        width: 100%;
        max-width: 400px;
        border-collapse: collapse;
        margin: 0 auto;
        border-top: 1px solid #f3e0e0;
        border-bottom: 1px solid #f3e0e0;
    }
    th,
    td {
        width: 14.28%;
        padding: 10px;
        text-align: center;
        border: none;
    }
    th {
        font-weight: bold;
        color: #ccc;
    }
    td {
        height: 50px;
        color: #666;
    }
    td.dday {
        padding: unset;
    }
    td.dday span {
        padding: 0.9rem 1rem;
        background-color: #9c0d0daf;
        border-radius: 100%;
        color: #fff;
        font-weight: bold;
    }
    .sunday {
        color: #f59999;
    }
    .saturday {
        color: #a1a1f2;
    }
</style>
