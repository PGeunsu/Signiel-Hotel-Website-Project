# π¨ Signiel-Hotel-Website-Project
κ°μ€ μμ½ μ¬μ΄νΈ (κ°μΈ νλ‘μ νΈ)

<br>

## π₯οΈ νλ‘μ νΈ μκ° 
μκ·Έλμ μμΈ μΉμ¬μ΄νΈ ν΄λ‘  μ½λ© λ° κ°μ€ μμ½ μ¬μ΄νΈ μλλ€ 
<br>

>πΊ π₯ [κΈ°λ₯ κ΅¬ν μμ](https://drive.google.com/file/d/1DszZpN0sRuT7cT4lxNiBSN7y7R2YeiN3/view?usp=share_link)


<br>

## π νλ‘μ νΈ κΈ°κ° <br>
22.10.17 ~ 22.11.04 (1μΈ)

<br>

## β¨οΈ κ°λ° νκ²½
* OS : Window
* Tool : Eclipse, HeidiSQL, Git
* Front-End : JSP, CSS, JavaSCript,Jquery
* Back-End : Java(1.8.0), ApacheTomcat
* DataBase : MySQL

<br>

## π±οΈ κΈ°λ₯ κ΅¬ν
1. νμκ°μ λ° λ‘κ·ΈμΈ, λ‘κ·Έμμ
2. νμ μμ  λ° νν΄
3. μμ΄λ, μ΄λ©μΌ μ€λ³΅κ²μ¬
4. κ²μκΈ μμ± λ° μμ ,μ­μ 
5. κ²μκΈ κ²μ
6. κ°μ€ μμ½
7. μμ½ λ΄μ­ μ‘°ν λ° μ·¨μ

<br>

## π‘ μμΈ κΈ°λ₯ μ€λͺ π‘

### λͺ©μ°¨
* [λ©μΈνλ©΄](#-λ©μΈνλ©΄)
* [νμκ°μ](#-νμκ°μ)
* [λ‘κ·ΈμΈ λ° νμμμ ](#-λ‘κ·ΈμΈ-λ°-νμμμ )
* [μμ½ κΈ°λ₯](#-μμ½-κΈ°λ₯)
* [μμ½ μ‘°ν λ° μ·¨μ](#-μμ½-μ‘°ν-λ°-μ·¨μ)

<br>

## π λ©μΈνλ©΄
![αα¦αα΅α«ααͺαα§α«](https://user-images.githubusercontent.com/110580350/210519095-85b15747-7e8c-43af-961d-3aa358091a92.gif)

### AutoSwiper
```javaScript
	 var swiper = new Swiper(".mySwiper", {
        spaceBetween: 30,
        centeredSlides: true,
        autoplay: {
          delay: 3000,
          disableOnInteraction: false,
        },
        loop : true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
      });
```

### νμ¬ λ μ¨ λ° κΈ°μ¨
```javaScript
<script>
	 $.getJSON(
	            "https://api.openweathermap.org/data/2.5/weatherid=1835848&appid=079b8942e0b5aa9292436aca492ee8f0&units=metric",
    function (data) {

        var $cTemp = data.main.temp;


        $(".ctemp").prepend($cTemp);

        var $now = new Date();
        var $cDate = $now.getFullYear() + "λ" + ($now.getMonth() + 1) + "μ" + $now.getDate()
            + "μΌ " + $now.getHours() + " : " + $now.getMinutes() + "\n";

        $(".cDate")	.prepend($cDate);
    }
);
	
	</script>
```

### Map API 
```javaScript
//Kakao Map API μ λ£νλ‘ μΈνμ¬ νμ μλ¨
 <script type="text/javascript" src="https://dapi.kakao.com/v2/maps/sdk.js?appkey=25865c9220776c3ab30a64088a76e6db"></script>
             <script>
      var mapContainer = document.getElementById('map'), // μ§λλ₯Ό νμν  div 
          mapOption = {
              center: new kakao.maps.LatLng(37.8282, 127.0685), // μ§λμ μ€μ¬μ’ν
              level: 5 // μ§λμ νλ λ λ²¨
          };

      // μ§λλ₯Ό νμν  divμ  μ§λ μ΅μμΌλ‘  μ§λλ₯Ό μμ±ν©λλ€
      var map = new kakao.maps.Map(mapContainer, mapOption); 
  </script>
```

<br>

## π νμκ°μ
![αα¬αα―α«αα‘αα΅αΈ](https://user-images.githubusercontent.com/110580350/210520632-194ecd48-c930-47f3-91d6-916fb5debee6.gif)

### νμ μΆκ°
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql"%>
<%
	request.setCharacterEncoding("UTF-8");
	
	String id = request.getParameter("userID");
	String password = request.getParameter("userPassword");
	String email = request.getParameter("userEmail");
	String firstName = request.getParameter("userEnFirstName");
	String lastName = request.getParameter("userEnLastName");
	String koName = request.getParameter("userKoName");
	String birth = request.getParameter("userBirth");	
	String number = request.getParameter("userNumber");
%>
	<sql:setDataSource var="dataSource"
		url="jdbc:mysql://localhost:3307/ProjectDB"
		driver="com.mysql.jdbc.Driver" user="root" password="1234" />
	<sql:update dataSource="${dataSource}" var="resultSet">
		INSERT INTO member VALUES (?,?,?,?,?,?,?,?)
		<sql:param value="<%=id%>" />
		<sql:param value="<%=password%>" />
		<sql:param value="<%=email%>" />
		<sql:param value="<%=firstName%>" />
		<sql:param value="<%=lastName%>" />
		<sql:param value="<%=koName%>" />
		<sql:param value="<%=birth%>" />
		<sql:param value="<%=number%>" />
	</sql:update>	
```
### μμ΄λ,μ΄λ©μΌ μ€λ³΅νμΈ
```jsp
String sql = "select * from member where UserID = ?";
	pstmt = conn.prepareStatement(sql);
	pstmt.setString(1, id);
	rs = pstmt.executeQuery();
<%
		if(rs.next()){%>
		<script>
			alert("μ€λ³΅λ μμ΄λμλλ€.");
			location.href = "signup.jsp"; //νμκ°μ νλ©΄μΌλ‘ μ΄λ ν μ΄κΈ°ν
		</script>
	<%
		}else{%>
		<script>
			alert("μ¬μ©κ°λ₯ν μμ΄λ μλλ€.")	
			window.history.back(); // λ€λ‘κ°κΈ°
		</script>
		<%} %>
    
    String sql = "select * from member where userEmail = ?";
	pstmt = conn.prepareStatement(sql);
	pstmt.setString(1, email);
	rs = pstmt.executeQuery();
	
%>
<%
		if(rs.next()){%>
		<script>
			alert("μ€λ³΅λ μ΄λ©μΌμλλ€.");
			location.href = "signup.jsp";
		</script>
	<%
		}else{%>
		<script>
			alert("μ¬μ©κ°λ₯ν μ΄λ©μΌ μλλ€.")	
			window.history.back();
		</script>
		<%} %>
```

## π λ‘κ·ΈμΈ λ° νμμμ 
![αα©αα³αα΅α«-αα΅αΎ-αα¬αα―α«-αα?αα₯αΌ-_](https://user-images.githubusercontent.com/110580350/210522155-fbbb9488-aa65-4ce0-8d4b-f39a9eff57d6.gif)

### λ‘κ·ΈμΈ
```jsp
<%
	request.setCharacterEncoding("UTF-8");

	String id = request.getParameter("userID");
	String password = request.getParameter("userPassword");
	
%>
	<sql:setDataSource var="dataSource" url="jdbc:mysql://localhost:3307/ProjectDB"
	driver="com.mysql.jdbc.Driver" user="root" password="1234" />
	
	<!-- sqlμΏΌλ¦¬λ¬Έ μ€ννλ μ½λ. executeQuery() -->
	<sql:query dataSource="${dataSource}" var="resultSet">
	SELECT * FROM MEMBER WHERE userID =? and userPassword=?  
		<sql:param value="<%=id%>"/>
		<sql:param value="<%=password%>"/>
	</sql:query>
	
	<c:forEach var="row" items="${resultSet.rows}">
		<%
			session.setAttribute("sessionId",id);
			//λ‘κ·ΈμΈμ΄ λλ©΄ μ¬μ©μ μμ΄λλ₯Ό μΈμμ μ€μ (μ μ₯)
		%>
		<c:redirect url="resultMember.jsp?msg=2"/>
		<!-- λ‘κ·ΈμΈ μλ―Έλ‘ μ¬μ©ν  κ² -->
	</c:forEach>
```

### λ‘κ·Έμμ
```jsp
<%
	session.invalidate();//session μ­μ νλ©΄ λ‘κ·Έμμ
	response.sendRedirect("login.jsp");
%>
```

### νμ μμ 
```jsp
<%
	request.setCharacterEncoding("UTF-8");
	
String id = request.getParameter("userID");
String password = request.getParameter("userPassword");
String email = request.getParameter("userEmail");
String firstName = request.getParameter("userEnFirstName");
String lastName = request.getParameter("userEnLastName");
String koName = request.getParameter("userKoName");
String birth = request.getParameter("userBirth");	
String number = request.getParameter("userNumber");
%>
	<sql:setDataSource var="dataSource"
		url="jdbc:mysql://localhost:3307/ProjectDB"
		driver="com.mysql.jdbc.Driver" user="root" password="1234" />
	<sql:update dataSource="${dataSource}" var="resultSet">
		update member set userEmail=?, userPassword=?, userEnFirstName=?, userEnLastName=?, userKoName=?, userBirth=?, userNumber=? where userID = ?
		<sql:param value="<%=email%>" />
		<sql:param value="<%=password%>" />
		<sql:param value="<%=firstName%>" />
		<sql:param value="<%=lastName%>" />
		<sql:param value="<%=koName%>" />
		<sql:param value="<%=birth%>" />
		<sql:param value="<%=number%>" />
		<sql:param value="<%=id%>" />
	</sql:update>	
```

### νμ νν΄
```jsp
<%
	String sessionId = (String) session.getAttribute("sessionId");
	
%>
	<sql:setDataSource var="dataSource" url="jdbc:mysql://localhost:3307/ProjectDB"
	driver="com.mysql.jdbc.Driver" user="root" password="1234" />
	
	<!-- sqlμΏΌλ¦¬λ¬Έ μ€ννλ μ½λ. executeQuery() -->
	<sql:update dataSource="${dataSource}" var="resultSet">
		delete from member where userID = ?
		<sql:param value="<%=sessionId %>"/>
	</sql:update>
	
	<c:if test="${resultSet >= 1 }">
		<c:import var="url" url="login.jsp"/>
		<c:redirect url="resultMember.jsp"/>
	</c:if>
```

<br>

## π κ²μν κΈ°λ₯ 
![αα¦αα΅αα‘α«](https://user-images.githubusercontent.com/110580350/210522812-9d201a0f-c053-49ee-ac6e-aa9cc73e5189.gif)

Controllerμ Commandλ‘ λλ μ κ΅¬λΆ

### Controller
```java
	public class BoardController extends HttpServlet {
		   private static final long serialVersionUID = 1L;
		 
		    public BoardController() {
		        
		    }


		   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		      actionDo(request, response);      
		   }

		   
		   protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		      actionDo(request, response);
		   }
		   
		   
		   private void actionDo(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		      System.out.println("actionDo");
		      
		      String uri = request.getRequestURI();
		      String contextPath = request.getContextPath();
		      String command = uri.substring(contextPath.length());
		      response.setContentType("text/html; charse=utf-8");
		      request.setCharacterEncoding("UTF-8");
		      
		      BCommand com = null;
		      String viewPage = null;
		      
		    //command ν¨ν΄μ λ°λΌμ λΆκΈ°ν¨
		      if(command.equals("/boardListAction.do")) {
					
		    	  com = new BListCommand();
		    	  com.execute(request, response);
		    	  viewPage = "./board/list.jsp";
		    	  
		      }else if(command.equals("/boardWriteForm.do")) {
					
					com = new BWriteFormCommand();
					com.execute(request, response);	
					viewPage = "./board/writeForm.jsp";
					
			  }else if(command.equals("/boardWriteAction.do")) {
					
					com = new BWriteCommand();
					com.execute(request, response);
					viewPage = "/boardListAction.do";
					
				}else if(command.equals("/boardViewAction.do")) {      //κ²μνμ μλ κ²μλ¬Ό μ λͺ© ν΄λ¦­νμ¬ μμΈλ΄μ©λ³΄λ λΆλΆ
					
			         com = new BViewCommand();
			         com.execute(request, response);
			      
			         
			         viewPage = "./board/view.jsp";
			      }else if(command.equals("/boardUpdateAction.do")) {      //κ²μνμ μλ κ²μλ¬Ό μ λͺ© ν΄λ¦­νμ¬ μμΈλ΄μ©λ³΄λ λΆλΆ
						
	                     com = new BUpdateCommand();
	                     com.execute(request, response);
	                     viewPage = "/boardListAction.do";
                  }else if(command.equals("/boardDeleteAction.do")) {      //κ²μνμ μλ κ²μλ¬Ό μ λͺ© ν΄λ¦­νμ¬ μμΈλ΄μ©λ³΄λ λΆλΆ
                        
                         com = new BDeleteCommand();
                         com.execute(request, response);
                         viewPage = "/boardListAction.do";
                      } 
		      //μμ λΆκΈ°λ¬Έμμ μ€μ λ view(.jsp)νμΌλ‘ νμ΄μ§ μ΄λ
		      RequestDispatcher rDispatcher = request.getRequestDispatcher(viewPage);
		      rDispatcher.forward(request, response);
		      
		      
		   }
```

### Command

#### κ²μν μμ±
```java
public class BWriteCommand implements BCommand {
	// κ²μκΈμ μμ±νκ³  κ·Έ κ²μκΈμ DBμ μ μ₯ν΄μ£Όλ μ»€λ§¨λ κ°μ²΄
	@Override
	public void execute(HttpServletRequest request, HttpServletResponse response) {

		BoardDAO bDAO = BoardDAO.getInstance();
		BoardDTO boardDTO = new BoardDTO();
		

		boardDTO.setId(request.getParameter("id"));
		boardDTO.setName(request.getParameter("name"));
		boardDTO.setSubject(request.getParameter("subject"));
		boardDTO.setContent(request.getParameter("content"));

		SimpleDateFormat sFormat = new SimpleDateFormat("yyyyλ MMμ ddμΌ");
		String regist_day = sFormat.format(new Date());

		boardDTO.setRegist_day(regist_day);
		boardDTO.setHit(0);
		boardDTO.setIp(request.getRemoteAddr());
		bDAO.insertBoard(boardDTO); // DBμ μ μ₯νλ λ©μλ νΈμΆ
	}
```
#### κ²μν λͺ©λ‘ 
```java
public class BListCommand implements BCommand {
	
	@Override
	public void execute(HttpServletRequest request, HttpServletResponse response) {
	// κ²μν λ¦¬μ€νΈλ₯Ό μ§μ μ μΌλ‘ κ°μ Έμ€λ μ»€λ§¨λ κ°μ²΄	
		BoardDAO bDao =  BoardDAO.getInstance();
		ArrayList<BoardDTO> boardlist = new ArrayList<>();
		
		int pageNum = 1;
		int limit = 5;			//ννμ΄μ§μ λνλΌ κ²μκΈ μ
		
		if(request.getParameter("pageNum") != null) {
			pageNum = Integer.parseInt(request.getParameter("pageNum"));
			//νμ΄μ§ κ°μ΄ nullμ΄ μλλΌλ©΄ ν΄λΉ νμ΄μ§λ₯Ό μ«μλ‘ λ³ννμ¬ μ μ₯ν¨.
		}	
		String items = request.getParameter("items");					//μ λͺ©,λ³Έλ¬Έ, κΈμ΄μ΄
		String text = request.getParameter("text");						//κ²μμ΄
		
		int totalRecord = bDao.getListCount(items, text);				//DBμ μ₯λμ΄ μλ κ²μκΈ μ΄ κ°―μ
		boardlist = bDao.getBoardList(pageNum, limit, items, text);// dbμ μ μ₯λμ΄ μλ μ€μ  κ²μκΈ κ°μ Έμ΄
		
		// ννμ΄μ§ μ κ΅¬νκΈ°
		int totalPage = 1;
		
		if(totalPage % limit == 0) {
			totalPage = totalRecord / limit;
			Math.floor(totalPage);
		}else {
			totalPage = totalRecord / limit;
			Math.floor(totalPage);
			totalPage += 1;
		}
		//Request κ°μ²΄μ κ°κ° ν΄λΉνλ κ° μ μ₯
		request.setAttribute("pageNum", pageNum);
		request.setAttribute("totalPage", totalPage);
		request.setAttribute("totalRecord", totalRecord);
		request.setAttribute("boardList", boardlist);

		
	}


}
```

#### κ²μν μμΈλ³΄κΈ° 
```java
public class BViewCommand implements BCommand {

	@Override
	public void execute(HttpServletRequest request, HttpServletResponse response) {
		// TODO Auto-generated method stub
		BoardDAO bDao = BoardDAO.getInstance();
		
		int num = Integer.parseInt(request.getParameter("num"));
		//λ³΄κ³ μ νλ λ²νΈ
		int pageNum = Integer.parseInt(request.getParameter("pageNum"));
		//λ³΄κ³ μνλ κ²μκΈμ΄ μλ νμ΄μ§μ
		BoardDTO boardDTO = new BoardDTO();
		boardDTO =  bDao.getBoardByNum(num, pageNum);
		
		request.setAttribute("num", num);
		request.setAttribute("pageNum", pageNum);
		request.setAttribute("boardDTO", boardDTO);
		
		
		
	}
```

#### κ²μν μμ  λ° μ­μ 
```java
public class BUpdateCommand implements BCommand{
 @Override
    public void execute(HttpServletRequest request, HttpServletResponse response) {
      
        int num = Integer.parseInt(request.getParameter("num"));
        
        BoardDAO bDao = BoardDAO.getInstance();
        BoardDTO boardDTO = new BoardDTO();
        
        boardDTO.setNum(num);
        boardDTO.setSubject(request.getParameter("subject"));
        boardDTO.setContent(request.getParameter("content"));
        
        SimpleDateFormat sFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String regist_day = sFormat.format(new Date());
        
        boardDTO.setRegist_day(regist_day);
        boardDTO.setIp(request.getRemoteAddr());   
        
        bDao.updateBoard(boardDTO);
    }
  }
    
    public class BDeleteCommand implements BCommand {

    @Override
    public void execute(HttpServletRequest request, HttpServletResponse response) {
      
        int num = Integer.parseInt(request.getParameter("num"));
        
        BoardDAO bDao = BoardDAO.getInstance();
        bDao.deleteBoard(num);
        
    }

}
```

<br>

## π μμ½ κΈ°λ₯
![αα¨αα£α¨αα΅αα³αΌ](https://user-images.githubusercontent.com/110580350/210523871-a3947ea8-823a-4dfc-960d-f3da2738f4e3.gif)

### μμ½ λ μ§ λ° κ°μ€ μ ν
```java
@WebServlet(urlPatterns = {"/reservation/reserveroom"})
public class ReservationRoomServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	/**
	 * reservation - reservation1.jspμμ μνλ ν¬μ λ μ§, μΈμμ μ λ³΄λ₯Ό λ°μ reservation2.jspμκ² μ‘°κ±΄μ λ§λ κ°μ€ μ λ³΄λ₯Ό μ μ‘
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String r_checkin = request.getParameter("r_checkin");
		String r_checkout = request.getParameter("r_checkout");
		int r_adults = Integer.parseInt(request.getParameter("r_adults"));
		int r_kids = Integer.parseInt(request.getParameter("r_kids"));	

		String msg = "";
		ReservationDAO rDAO = new ReservationDAO();
		ArrayList<RoomDTO> room_type = rDAO.selectRoomByPeople(r_adults+r_kids);
		ArrayList<RoomDTO> totalroom = rDAO.selectRoomByDate(room_type, r_checkin, r_checkout);
		
		if(totalroom.size()==0){
			msg = "μμ½ κ°λ₯νμ  λ°©μ΄ μμ΅λλ€.λ€μ μ νν΄μ£ΌμΈμ";
		}
		
		String  str = "yyyy-MM-dd";
		SimpleDateFormat sdf = new SimpleDateFormat(str);
		long diffday = 0;
		try {
			Date checkin = sdf.parse(r_checkin);
			Date checkout = sdf.parse(r_checkout);
			
			diffday = (checkout .getTime() - checkin.getTime()) / (24*60*60*1000);
		
		} catch (ParseException e) {
			System.err.println("ReservationRoomServlet - doGet() err : " + e.getMessage());
		}
		
		request.setAttribute("diffday", diffday);
		request.setAttribute("r_checkin", r_checkin);
		request.setAttribute("r_checkout", r_checkout);
		request.setAttribute("r_adults", r_adults);
		request.setAttribute("r_kids", r_kids);
		request.setAttribute("totalroom", totalroom);
		request.setAttribute("msg", msg);
		
		RequestDispatcher rd = request.getRequestDispatcher("reservation2.jsp");
		rd.forward(request, response);
		
	}
```

### μ΅μ μ ν ν μμ½ νμ 
```java
/**
	 *  reservation - reservation3.jsp μμ μμ½μ κ΄λ ¨λ λͺ¨λ  μ λ³΄λ₯Ό κ°μ Έμ dbμ μ μ₯ν μμ½ μλ£ μ¬λΆ κ²°κ³Όλ₯Ό reservationProc.jsp μκ² μ λ¬
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		request.setCharacterEncoding("UTF-8");
		HttpSession session = request.getSession();
		String r_id = (String)session.getAttribute("sessionId");
		int r_adults = Integer.parseInt(request.getParameter("r_adults"));
		int r_kids = Integer.parseInt(request.getParameter("r_kids"));
		String r_checkin = request.getParameter("r_checkin");
		String r_checkout = request.getParameter("r_checkout");
		String r_type = request.getParameter("r_type");
		int r_price = Integer.parseInt(request.getParameter("r_price"));
		
		ReservationDTO r = new ReservationDTO();
		r.setR_id(r_id);
		r.setR_adults(r_adults);
		r.setR_kids(r_kids);
		r.setR_checkin(r_checkin);
		r.setR_checkout(r_checkout);
		r.setR_type(r_type);
		r.setR_price(r_price);

		ReservationDAO dao = new ReservationDAO();
		int result = dao.insertRoom(r);
		
		request.setAttribute("result", result);
		RequestDispatcher rd = request.getRequestDispatcher("reservationProc.jsp");
		rd.forward(request, response);
	}
```
<br>

## π μμ½ μ‘°ν λ° μ·¨μ
![αα¨αα£α¨-αα©αα¬-αα΅αΎ-αα±αα©](https://user-images.githubusercontent.com/110580350/210525529-7c193adb-8e97-44cf-852e-9b090091a88f.gif)

### μμ½ μ‘°ν
```java
@WebServlet(urlPatterns= {"/reservation/reserveinfo"})
public class UserReserveInfoServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	/**
	 * κ° header.jspμμ μμ½λ΄μ­ ν΄λ¦­μ νμμ μμ½λ΄μ­ μ λ³΄λ₯Ό reservation - reserveInfo.jspμκ² μ λ¬ 
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		HttpSession session = request.getSession();
		String sessionId = (String)session.getAttribute("sessionId");
		ReservationDAO dao = new ReservationDAO();
		ArrayList<ReservationDTO> dto = dao.selectReservation(sessionId);

		request.setAttribute("dto", dto);
		RequestDispatcher rd = request.getRequestDispatcher("/reservation/reserveInfo.jsp");
		rd.forward(request, response);
	}

	/**
	 * user - reserveInfo.jspμμ μμ½μ·¨μ λ²νΌ ν΄λ¦­μ νμμ λͺ¨λ  μμ½ μ λ³΄λ₯Ό reserveCancel.jspμκ² μ λ¬
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		HttpSession session = request.getSession();
		String sessionId = (String)session.getAttribute("sessionId");
		ReservationDAO dao = new ReservationDAO();
		ArrayList<ReservationDTO> dto = dao.selectReservation(sessionId);
		
		request.setAttribute("dto", dto);
		RequestDispatcher rd = request.getRequestDispatcher("/reservation/reserveCancel.jsp");
		rd.forward(request, response);
	}

}
```

### μμ½ μ·¨μ
```java
@WebServlet(urlPatterns= {"/reservation/reservecancel"})
public class UserReserveCancelServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	/**
	 * user - reserveCancel.jspμμ μ²΄ν¬λ μμ½λ΄μ­ λ²νΈλ€μ κ°μ Έμμ dbμ μ μ₯λ μμ½ λ΄μ­μ μ­μ  ν reserveInfo.jspλ‘ μ΄λ
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String[] r_number = request.getParameterValues("reserve");
		int[] r_numbers = Arrays.stream(r_number).mapToInt(Integer::parseInt).toArray();
		
		ReservationDAO rdao = new ReservationDAO();
		int num = rdao.cancelReservation(r_numbers);
		request.setAttribute("num", num);

		RequestDispatcher rd = request.getRequestDispatcher("reserveinfo");
		rd.forward(request, response);
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}

}
```
