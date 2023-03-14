### useMemo
> 함수 컴포넌트 내부에서 발생하는 연산을 최적화 할 수 있음


### before use
```
import { useState} from "react";

const getAverage = number => {
    console.log('평균값 계산중..');
    if(number.length === 0) return 0;
    const sum = number.reduce((a,b) => a + b);
    return sum / number.length;
}

const Average = () => {
    const [list,setList] = useState([]);
    const [number,setNumber] = useState('');

    const onChange = e => {
        setNumber(e.target.value);
    };
    const onInsert = e => {
        const nextList = list.concat(parseInt(number));
        setList(nextList);
        setNumber('');
    };

    return(
        <div>
            <input value={number} onChange={onChange} />
            <button onClick={onInsert}>등록</button>
            <ul>
                {list.map((value,index) => (
                    <li key={index}>{value}</li>
                ))}
            </ul>
            <div>
                <b>평균값:</b>{getAverage(list)}
            </div>
        </div>
    )
}


export default Average;

//등록뿐 아니라 input의 value가 수정될 때도 getAverage()가됨호출됨
```
### after use
```
import { useState,useMemo} from "react";

const getAverage = number => {
    console.log('평균값 계산중..');
    if(number.length === 0) return 0;
    const sum = number.reduce((a,b) => a + b);
    return sum / number.length;
}

const Average = () => {
    const [list,setList] = useState([]);
    const [number,setNumber] = useState('');

    const onChange = e => {
        setNumber(e.target.value);
    };
    const onInsert = e => {
        const nextList = list.concat(parseInt(number));
        setList(nextList);
        setNumber('');
    };
    const avg = useMemo(() => getAverage(list),[list])
    return(
        <div>
            <input value={number} onChange={onChange} />
            <button onClick={onInsert}>등록</button>
            <ul>
                {list.map((value,index) => (
                    <li key={index}>{value}</li>
                ))}
            </ul>
            <div>
                <b>평균값:</b>{avg}
            </div>
        </div>
    )
}


export default Average;

//list배열의 내용이 바뀔 때만 getAverage()가 
```
