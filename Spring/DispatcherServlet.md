요청이 들어오면 web.xml -> dispatcherservlet이 동작   
dispatcherservlet은 frontController + requestDispatcher의 결합   
dispatcherservlet은 주소분배를 하는 역할을한다.   
분배를 하려면 메모리에 떠있어야한다. 주소를 분배하기 전에    
dispatcherservlet이 컴포넌트 스캔을 통해서 src폴더 내부에 있는 모든 (애노테이션이 붙어있는) java파일들을 다 찾아서   
메모리에 띄운다.    
@Controller   
@RestController  
@Service   
@Repository  
@Component   
@Configration   
등등..   
