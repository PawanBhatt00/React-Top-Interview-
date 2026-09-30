# React.js — 50 Interview Questions (Hinglish Explanation)

<details><summary>1. React kya hai aur use kyun karte hain?</summary>

React ek JavaScript library hai jo UI banane ke liye use hoti hai. Ye component-based aur declarative approach follow karti hai, aur Virtual DOM use karti hai taaki updates fast ho sakein. Log ise isliye pasand karte hain kyunki components reusable hote hain, ecosystem bahut bada hai, aur one-way data flow ki wajah se state predictable rehti hai.
</details>

<details><summary>2. Virtual DOM kya hai aur ye performance kaise improve karta hai?</summary>

Virtual DOM asal DOM ka ek lightweight, in-memory copy hota hai. React naya virtual DOM purane wale se compare (diff) karta hai — is process ko reconciliation kehte hain — aur sirf wahi minimum changes real DOM me apply karta hai. Isse pura page baar-baar re-render nahi hota, jo performance ke liye bahut fayda karta hai.
</details>

<details><summary>3. JSX kya hai?</summary>

JSX ek syntax extension hai jisme aap JavaScript ke andar HTML jaisa markup likh sakte ho. Babel is JSX code ko compile karke `React.createElement()` calls me convert kar deta hai.
</details>

<details><summary>4. Functional aur class components me kya farak hai?</summary>

Functional components simple functions hote hain jo state/lifecycle handle karne ke liye Hooks use karte hain. Class components `React.Component` ko extend karte hain aur `this.state` + lifecycle methods use karte hain. Aajkal Functional components + Hooks hi standard approach hai.
</details>

<details><summary>5. Props aur state me kya difference hai?</summary>

Props parent se child ko milne wala data hota hai jo read-only hota hai (child usse change nahi kar sakta). State component ke andar ka internal data hota hai jo change ho sakta hai, aur jab change hota hai to component re-render hota hai.
</details>

<details><summary>6. Class components ka lifecycle samjhao.</summary>

Teen phases hote hain — Mounting (`constructor`, `render`, `componentDidMount`), Updating (`shouldComponentUpdate`, `render`, `componentDidUpdate`), aur Unmounting (`componentWillUnmount`). Error handle karne ke liye `componentDidCatch` aur `getDerivedStateFromError` bhi hote hain.
</details>

<details><summary>7. `useState` kya hai aur ye kaise kaam karta hai?</summary>

Ye ek Hook hai jo functional component me local state add karta hai. Ye ek array return karta hai `[value, setter]` — value current state hoti hai, aur setter function call karne se naye value ke saath component re-render ho jata hai. React kabhi-kabhi multiple updates ko batch bhi kar deta hai.
</details>

<details><summary>8. `useEffect` kya hai aur uska dependency array kaise kaam karta hai?</summary>

`useEffect` side effects (jaise data fetching, subscriptions, DOM changes) handle karne ke liye use hota hai, aur render ke baad chalta hai. Dependency array control karta hai ki ye kab-kab chalega: `[]` sirf mount pe ek baar chalega, kuch na do to har render pe chalega, aur `[dep]` de do to sirf tab chalega jab `dep` change ho. Agar ek function return karo to wo cleanup ke liye use hota hai (next run ya unmount se pehle).
</details>

<details><summary>9. `useEffect` aur `useLayoutEffect` me kya difference hai?</summary>

`useEffect` browser paint hone ke baad asynchronously chalta hai. `useLayoutEffect` DOM change hone ke turant baad, paint hone se pehle synchronously chalta hai — ye tab use karte hain jab screen pe flicker dikhne se pehle DOM ko measure ya modify karna ho.
</details>

<details><summary>10. `useContext` kya hai aur kab use karna chahiye?</summary>

Ye Hook Context ki value ko directly use karne deta hai bina prop drilling ke. Jab koi data (jaise theme, logged-in user, language) bahut saare components me share karna ho, tab `useContext` useful hota hai.
</details>

<details><summary>11. `useRef` ka use kya hota hai?</summary>

`useRef` ek mutable value store karta hai jo renders ke beech persist rehti hai, aur usko change karne se re-render bhi nahi hota. Isse DOM element ka direct reference bhi mil jata hai.
</details>

<details><summary>12. `useMemo` aur `useCallback` me kya difference hai?</summary>

`useMemo` ek computed value ko memoize (yaad) karta hai, aur sirf tab dobara calculate karta hai jab dependencies change ho. `useCallback` ek function reference ko memoize karta hai, taaki wo function baar-baar naya na bane — isse child components unnecessary re-render nahi hote.
</details>

<details><summary>13. Custom Hooks kya hote hain aur inhe kyun banate hain?</summary>

Custom Hooks aise functions hote hain jinke naam `use` se start hote hain (jaise `useFetch`, `useForm`), jo built-in Hooks ko combine karke reusable logic banate hain. Isse code multiple components me reuse ho sakta hai, bina HOC ya render props jaisi complex cheezein use kiye.
</details>

<details><summary>14. Hooks ke rules kya hain?</summary>

Do main rules: Hooks ko sirf top level pe call karo (loops, conditions, ya nested functions ke andar nahi), aur Hooks sirf React function components ya custom Hooks ke andar hi call karo. Isse har render me Hooks ka call order same rehta hai.
</details>

<details><summary>15. Prop drilling kya hai aur ise kaise avoid karein?</summary>

Prop drilling tab hoti hai jab aap props ko bahut saare intermediate components se hote hue pass karte ho, jinhe unki jarurat nahi hoti, sirf ek deep nested child tak pahunchane ke liye. Ise avoid karne ke liye Context API, state management libraries (Redux), ya component composition use kar sakte hain.
</details>

<details><summary>16. "Lifting state up" kya hota hai?</summary>

Jab shared state ko usse jarurat wale components ke closest common parent me move kar diya jata hai, aur phir props ke through niche pass kiya jata hai — taaki saare components sync me rahein.
</details>

<details><summary>17. React me reconciliation kya hai?</summary>

Ye wo algorithm hai jisse React naye virtual DOM tree ko purane se compare karta hai aur decide karta hai ki real DOM me minimum kya changes karne hain. Ye element type aur `key` props jaisi heuristics use karta hai.
</details>

<details><summary>18. Lists me `key` prop itna important kyun hai?</summary>

Key React ko har list item ki ek stable identity deta hai, jisse React renders ke beech items ko sahi tarike se reorder, update ya remove kar sake, bina pure list ko re-render kiye. Array index ko key banane se bugs aa sakte hain jab items reorder ya insert hote hain.
</details>

<details><summary>19. Conditional rendering kya hai? Kuch patterns batao.</summary>

State ya props ke basis pe different UI render karna conditional rendering kehlata hai. Patterns hote hain — ternary (`cond ? <A/> : <B/>`), `&&` short-circuit, early return, ya switch-jaisa lookup object.
</details>

<details><summary>20. Controlled aur uncontrolled components (forms) me kya farak hai?</summary>

Controlled component me input ki value React state se control hoti hai `value` aur `onChange` ke through. Uncontrolled component me DOM khud apni value manage karta hai, aur jarurat padne pe `ref` (jaise `useRef`) se value nikal lete hain.
</details>

<details><summary>21. React me forms kaise handle karte hain?</summary>

Aam taur pe controlled inputs use karte hain jinme `value` state se bind hota hai aur `onChange` se update hota hai. Ya phir form library (Formik, React Hook Form) use karte hain jo validation, error handling, aur kam re-renders provide karti hai.
</details>

<details><summary>22. React Router kya hai aur client-side routing kaise kaam karta hai?</summary>

React Router ek library hai jo SPA me declarative client-side navigation deti hai, `<Routes>`/`<Route>` jaise components se. Ye URL change ko History API se intercept karta hai aur matching component render kar deta hai, bina page reload kiye.
</details>

<details><summary>23. React Router ke `<Link>` aur normal `<a>` me kya difference hai?</summary>

`<Link>` History API use karke client-side navigation karta hai, isse full page reload nahi hota aur app ki state bani rehti hai. `<a>` tag full browser navigation/reload trigger karta hai.
</details>

<details><summary>24. React Fragments kya hain aur inhe kyun use karte hain?</summary>

`<>...</>` ya `<React.Fragment>` se aap multiple children ko group kar sakte ho bina koi extra DOM node add kiye — isse unnecessary wrapper `div`s avoid ho jate hain.
</details>

<details><summary>25. Context API kya hai aur iski limitations kya hain?</summary>

Context API ek built-in tarika hai data ko component tree me share karne ka, bina prop drilling ke. Limitation ye hai ki jab bhi context value change hoti hai, saare consumers re-render ho jate hain — agar updates bahut frequent hon aur memoization na ho, to performance pe asar padta hai.
</details>

<details><summary>26. Redux vs Context API — kab kya use karein?</summary>

Simple aur kam-kam change hone wale global data (jaise theme, auth) ke liye Context theek hai. Complex, frequently-updating state, middleware (logging, async calls), aur devtools/time-travel debugging ki jarurat ho to Redux (ya similar library) better hai.
</details>

<details><summary>27. Redux ke core concepts samjhao — store, actions, reducers.</summary>

Store app ki puri state ka single source of truth hota hai. Actions plain objects hote hain jo batate hain "kya hua hai". Reducers pure functions hote hain jo current state aur action lekar naya state return karte hain — store update karne ka yehi ek tarika hota hai.
</details>

<details><summary>28. Redux Toolkit kya hai aur ye kyun banaya gaya?</summary>

Redux Toolkit Redux likhne ka official aur asaan tarika hai. Ye `createSlice`, `configureStore` jaise tools se boilerplate kam karta hai, Immer ke through "mutable jaise dikhne wale" immutable updates deta hai, aur `createAsyncThunk` se async logic bhi built-in provide karta hai.
</details>

<details><summary>29. Redux me middleware (jaise thunk) kya hota hai?</summary>

Middleware ek function hota hai jo dispatch hue action ko reducer tak pahunchne se pehle intercept karta hai. Isse side effects handle hote hain — jaise `redux-thunk` action creators ko object ki jagah function return karne deta hai, jisse async calls ya logging possible hoti hai.
</details>

<details><summary>30. React.memo kya hai aur kab use karna chahiye?</summary>

React.memo ek higher-order component hai jo functional component ko memoize karta hai — agar props change nahi hue (shallow comparison), to component re-render skip ho jata hai. Ye tab useful hai jab koi expensive pure component parent ke re-render hone se unnecessarily re-render ho raha ho.
</details>

<details><summary>31. Unnecessary re-renders kis wajah se hote hain aur inhe kaise rokein?</summary>

Common reasons: har render pe naya object/array/function reference banna, unmemoized context value, ya state update ko jarurat se zyada upar rakhna. Inhe React.memo, useMemo/useCallback, aur state ko usi jagah rakh ke jahan use ho, se roka ja sakta hai.
</details>

<details><summary>32. Code-splitting aur `React.lazy`/`Suspense` kya hai?</summary>

Code-splitting bundle ko chote-chote parts me todta hai jo jarurat padne pe load hote hain. `React.lazy(() => import(...))` component ko lazily load karta hai, aur `<Suspense fallback={...}>` tab tak ek fallback UI dikhata hai jab tak component load nahi ho jata.
</details>

<details><summary>33. Error boundaries kya hote hain?</summary>

Ye class components hote hain jo `componentDidCatch` aur `getDerivedStateFromError` implement karte hain. Ye apne child tree me render ke time aane wale JS errors ko catch kar lete hain, taaki pura app crash na ho aur fallback UI dikha sakein.
</details>

<details><summary>34. `setX(v)` aur `setX(prev => ...)` me kya farak hai?</summary>

Agar value directly pass karo to fast/batched updates me purani (stale) closure value use ho sakti hai. Function pass karne se React aapko latest state value deta hai, jisse previous state pe depend karne wale updates sahi rehte hain — khaaskar jab ek se zyada baar update ho raha ho re-render se pehle.
</details>

<details><summary>35. React state updates ko kaise batch karta hai?</summary>

React ek hi event handler ke andar hone wale multiple `setState` calls ko (React 18 se async boundaries me bhi) ek single re-render me group kar deta hai, taaki har call pe alag se re-render na ho aur performance behtar rahe.
</details>

<details><summary>36. React me Portals kya hain?</summary>

`ReactDOM.createPortal(child, domNode)` ek child ko parent component ki DOM hierarchy se bahar kisi doosre DOM node me render karta hai. Ye modals aur tooltips banane me use hota hai jinhe overflow ya z-index restrictions se bahar nikalna hota hai.
</details>

<details><summary>37. Server-side rendering (SSR) kya hai aur React (Next.js) se iska kya relation hai?</summary>

SSR components ko server pe HTML me convert karke initial response bhejta hai, jisse loading fast lagti hai aur SEO bhi better hota hai. Uske baad client pe "hydration" hota hai jisse interactivity add hoti hai. Next.js is cheez ko React ke saath deta hai.
</details>

<details><summary>38. SSR ke context me hydration kya hai?</summary>

Hydration wo process hai jisme React server-rendered static HTML pe event listeners attach karta hai aur usse client-side virtual DOM ke saath reconcile karta hai, taaki page bina dobara se render kiye interactive ban jaye.
</details>

<details><summary>39. Higher-Order Components (HOCs) kya hote hain?</summary>

HOC ek function hota hai jo ek component leta hai aur ek naya enhanced component return karta hai — cross-cutting concerns (jaise `withAuth(Component)`) ke liye use hota hai. Aajkal iski jagah zyada tar custom Hooks use hote hain.
</details>

<details><summary>40. Render props pattern kya hai?</summary>

Ye ek technique hai jisme component ek function ko prop ki tarah accept karta hai (usually `render` ya `children` naam se) jo JSX return karta hai. Isse consumer decide karta hai ki kya render hona hai, aur component sirf shared logic/data deta hai.
</details>

<details><summary>41. React me data fetching kaise karte hain (library ke saath aur bina)?</summary>

Bina library ke: `fetch`/`axios` ko `useEffect` ke andar use karke result, loading, error state me store karte hain. Library ke saath: React Query ya RTK Query use karte hain, jo caching, deduping, background refetching, aur loading/error states khud handle kar deti hain.
</details>

<details><summary>42. React Query (TanStack Query) kya hai aur manual `useEffect` fetching se better kyun hai?</summary>

Ye ek data-fetching aur caching library hai jo server state manage karti hai — caching, background refetch, deduplication, retries, aur stale-time jaise features deti hai. Isse manual fetch-in-`useEffect` wale approach me aane wale bahut saare boilerplate aur bugs khatam ho jate hain.
</details>

<details><summary>43. RTK Query kya hai?</summary>

Redux Toolkit ka built-in data-fetching aur caching solution hai, jo API slice define karne pe khud hooks (`useGetXQuery`) generate kar deta hai — aur server-state caching ko directly Redux store ke saath integrate kar deta hai.
</details>

<details><summary>44. `useEffect` ka cleanup aur unmounting me kya difference hai?</summary>

`useEffect` se return hone wala cleanup function do situation me chalta hai — jab dependencies change hone ki wajah se effect dobara chalta hai, aur jab component unmount hota hai. Ye subscriptions, timers, ya requests cancel karne ke liye use hota hai taaki memory leaks ya stale updates na ho.
</details>

<details><summary>45. React me prop-types/TypeScript ka role kya hai aur props ko type-check karna kyun jaruri hai?</summary>

Ye props ke expected shape ko validate/document karte hain — TypeScript compile-time pe aur PropTypes runtime pe. Isse bugs jaldi pakde jate hain aur IDE ki autocompletion/refactoring bhi behtar hoti hai.
</details>

<details><summary>46. React DevTools ka use kya hai?</summary>

Ye ek browser extension hai jisse aap component tree, props/state ko inspect kar sakte ho, renders/performance profile kar sakte ho, aur ye pata laga sakte ho ki kaunse components unnecessarily re-render ho rahe hain.
</details>

<details><summary>47. `useState` aur `useReducer` me kya difference hai?</summary>

`useState` simple, independent state values ke liye theek hai. `useReducer` tab better hai jab state logic complex ho, multiple sub-values ho, ya next state previous state pe depend karta ho well-defined actions ke through (Redux jaisa, lekin local level pe).
</details>

<details><summary>48. React me bade lists ki rendering performance kaise optimize karein?</summary>

Windowing/virtualization use karo (jaise `react-window`/`react-virtualized`) jisse sirf visible rows render hon, stable `key`s use karo, aur row components ke liye `React.memo` use karo taaki puri list dobara render na ho.
</details>

<details><summary>49. Client-side rendering (CSR) aur SSR/SSG me kya difference hai?</summary>

CSR ek minimal HTML shell bhejta hai aur baaki sab kuch browser me JS se render hota hai (first paint slow hota hai, lekin highly interactive apps ke liye achha hai). SSR har request pe server pe render karta hai. SSG (Static Site Generation) pages ko build time pe hi pre-render kar deta hai — dono hi pure CSR se initial load aur SEO me behtar hain.
</details>

<details><summary>50. Ek mid-sized React project ka structure (folders/architecture) kaise banayenge?</summary>

Common approach hai feature-based folders banana — har feature ke apne components, hooks, API calls, aur slice ek jagah hon (type-based structure ki jagah, jisme sab components ek saath hote hain). Iske saath shared `components/`, `hooks/`, `utils/`, `api/` ya `services/` folders, aur ek central store/routing setup bhi rakhte hain.
</details>
